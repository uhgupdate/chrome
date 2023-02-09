# chrome

https://learn.microsoft.com/vi-vn/training/modules/monitor-azure-vm-using-diagnostic-data/3-exercise-create-virtual-machine


LOCATION=us
RESOURCEGROUP=maingroup

az group create \
--name $RESOURCEGROUP \
--location $LOCATION








STORAGE=metricsstorage$RANDOM

az storage account create \
    --name $STORAGE \
    --sku Standard_LRS \
    --location $LOCATION \
    --resource-group $RESOURCEGROUP
    
    
    
    
    
    
    
    
    
    
    
az vm create \
    --name monitored-linux-vm \
    --image UbuntuLTS \
    --size Standard_B1s \
    --location $LOCATION \
    --admin-username azureuser \
    --boot-diagnostics-storage $STORAGE \
    --resource-group $RESOURCEGROUP \
    --generate-ssh-keys
