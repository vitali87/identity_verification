# Design choices

- Data storage in cloud bucket
- Use Fireworks API for vision extraction
- Jailbreak the model to extract the data
- Use Pydantic for data validation
- Use OpenAI API for LLM
- JSON format for the response
- Productionize the API with FastAPI, Kubernetes

# Data storage in cloud bucket

Currently data was downloaded locally and processed. In prodcution, data should be storaged in cloud buckets like S3 which can provide direct links to the images that Fireworks AI can consume without the need to encode the image to base64.

# Fireworks API

Fireworks AI api support one of the best lightweight vision model phi-3-vision-128k-instruct which has 128k context length.

# Jailbreak

The model refused to extract person identity information from the image. So I had to jailbreak the model to extract the data. I understand this is probably meant for understanding if Fireworks AI vision models are susceptible to jailbreak. 

# Pydantic

Pydantic is a data validation library for Python. It is used to validate the data extracted from the image.

# OpenAI API

OpenAI API is used to provide more flexibility for swiitching between LLms and providers.

# JSON format

JSON format is used to format the response as the production system might expect a JSON format response for downstream processing.

# FastAPI

As I have done numerous times before, k8s with FastAPI api endpoint deployed on it can be used to productionize the system. However, due to limited time, I have not impelemented this part.
