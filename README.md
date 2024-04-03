# Azure ServiceBus example

## Create a Service Bus namespace, named "rokonet" in RessourceGroup "rg1"

## Create a Service Bus queue, named "salesmessages"

## Get the connection string to the Service Bus namespace
az servicebus namespace authorization-rule keys list `
    --resource-group rg1 `
    --name RootManageSharedAccessKey `
    --query primaryConnectionString `
    --output tsv `
    --namespace-name rokonet1

##  clone git repository
git clone https://github.com/MicrosoftDocs/mslearn-connect-services-together.git
git clone https://github.com/rokonet8/AzureServiceBusLab.git

## update connecntion string in "programm.cs"

## Send a message to the queue
dotnet run --project ./privatemessagesender

## get number of messages that are in the queue
az servicebus queue show `
    --resource-group rg1 `
    --name salesmessages `
    --query messageCount `
    --namespace-name rokonet

## Receive a message from the queue
dotnet run --project privatemessagereceiver

