# Gandalf Q&A embeddings

<!-- TOC -->

- [Gandalf Q&A embeddings](#openai-experiments)
  - [What is this ?](#what-is-this-)
<!-- /TOC -->

## What is this ?

This repo holds an experiment with OpenAI's Embeddings API inspired by this tutorial => https://platform.openai.com/docs/tutorials/web-qa-embeddings.

The idea here is to:

- retrieve each post contents and metadata
- turn the retrieved information into embeddings, which are vectors that represent a set of meaningful tokens
- turn the user's question into an embedding
- find the embedding that is closest to the user's question
- use a chat endpoint to answer the user's question with the found embedding

## Pre requisites

### all environments

- There is a `.env` file to create and fill at the root of the repo.

### Ubuntu

``` bash
sudo apt-get install unixodbc-dev
sudo apt-get install odbcinst
sudo apt-get install libodbc1
sudo apt-get install libodbc1:i386

curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/22.04/prod.list)"
sudo apt-get update
sudo apt-get install msodbcsql17

sudo chmod +rx /usr/lib/libmsodbcsql-17.so
```
... add the following lines at the end of `/etc/odbcinst.ini`:

```
[ODBC Driver 17 for SQL Server]
Description=Microsoft ODBC Driver 17 for SQL Server
Driver=/opt/microsoft/msodbcsql17/lib64/libmsodbcsql-17.8.so.1.1
UsageCount=1
```

