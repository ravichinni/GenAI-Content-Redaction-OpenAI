# Data Redaction using Generative AI
## Overview:  
Redaction of content is an important step in Data Engineering to remove PII/ Sensitive data before the data is further processed in the pipeline. There are many code libraries to achieve this.   
This code achieves it using Generative AI. When redacted the content is replaced with text of format [Redacted \<Data Type\>]. Example: An email **ravi@contoso.com** in the content would be replaced with **[Redacted Email]**. The type of content that was tested includes Email, Names of Individuals and Companies, Phone Numbers, Server Names, IP Addresses, Physical Addresses, Zip Codes and Passwords.

## Approach:
- Chat Completions API of the Azure OpenAI was used.
- A System message was provided to the prompt
- Also, one few shot example was used in the prompt.

## Example:
### Input:
From: Adele Vance <adele.vance@fabrikam.com>  
Sent: Wednesday, August 16, 2023 7:27:40 PM  
To: Grady Archie <grady.archie@m365supportgroup.com>  
Cc: Joni Sherma <joni.sherman@m365supportgroup.com>  
Subject: Re: Microsoft 365 Deployement for fabrikam.com  
   
Hi Grady,

I have shared our godaddy details in a separate email. Please check.

Thank you,
Adele

### Output:
From: [Redacted Name] <[Redacted Email]>  
Sent: Wednesday, August 16, 2023 7:27:40 PM  
To: [Redacted Name] <[Redacted Email]>  
Cc: [Redacted Name] <[Redacted Email]>  
Subject: Re: Microsoft 365 Deployement for [Redacted Company Name] 

Hi [Redacted Name],

I have shared our [Redacted Company Name] details in a separate email. Please check.

Thank you,  
[Redacted Name]


## Dev Setup: 
Please have the below: 
- VS Code
- Python, latest version
- Jupyter Notebook extensions for VS Code
- Python extensions for VS Code 
- Azure Open AI

## Usage:
- Install the pre-requisites per the Dev Setup section
- Create an Azure Open AI instance. 
- Create an Azure Open AI LLM Model based on gpt-35-turbo
- Create a .env file in the same folder as the notebook file and add the below values and save:
  - AZURE_OAI_ENDPOINT=https://{Azure OpenAI instance name}-poc.openai.azure.com/
  - AZURE_OAI_KEY={Azure OpenAI Key}
  - AZURE_OAI_MODEL={Azure OpenAI LLM model name, based on gpt-35-turbo}
- Setup the Python Virtual environment using "python -m venv .venv" 
- Activate the Python Virtual environment using ".\env_name\Scripts\activate"
- Install the required Python packages using "pip install -r requirements.txt"
- Please see the notebook [ContentRedaction.ipynb](ContentRedaction.ipynb) for further instructions
