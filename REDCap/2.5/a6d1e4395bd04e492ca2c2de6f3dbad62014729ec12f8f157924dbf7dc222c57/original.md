```
function delete_DAGs(; url=get_url(), token=get_token(), dags)
```

Create a New Folder in the File Repository

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `name`: name of the new folder (150 characters maximum)
  * `folder_id`: folder_id of the intended parent directory (default is top-level directory in File Repository)
  * `dag_id`: optionally restrict folder access to a Data Access Group
  * `role_id`: optionally restrict folder access to a User Role
