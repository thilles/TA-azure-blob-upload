# README

This is an add-on powered by the Splunk Add-on Builder.

It is a custom alert action which let's you upload the results of a scheduled Splunk report to a Azure Storage Blob of your choosing.

This can be useful if you have some data in Splunk which you would like export and vizualize other places, e.g. PowerBI.

Tested and verified with Python3 and Splunk 8.2.0.

## Limitations

The user owning the report needs to have a role with the `list_storage_passwords` capability (not in `user` role by default).
Adding this will however have other security implications. A better solution is to have a dedicated service user which owns the reports.

## Installation and setup

Pretty straightforward

1. Install only on SH or SHC (via SHD) and restart

2. Configure proxy settings (if needed)

## Configuring the alert action

Navigate to your report and enable its scheduling.

Note that the `Azure account key` is not hashed in the Splunk backend. For security reasons the Azure storage account in use should not hold any PII or other sensitive information.

| Element | What |
-----|------
| Blob file name | If you want to overwrite the report name |
| Azure account name | Your Azure storage account |
| Azure account key | See [Azure docs](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal#view-account-access-keys) on how to obtain | 
| Azure container | Where you would like to store the blob |


![Upload configuration](static/config_blob_upload.png)

## Troubleshooting 

Search `index=_internal source=*splunkd.log upload_to_azure_blob` to view results of script.

## Support

This add-on is provided without support, but is supported on a best-effort basis by the community.
Contributions and pull requests are more than welcome.

Official Git repository: https://github.com/thilles/TA-azure-blob-upload