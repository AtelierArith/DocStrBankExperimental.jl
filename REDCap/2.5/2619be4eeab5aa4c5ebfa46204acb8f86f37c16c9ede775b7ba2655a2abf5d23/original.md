```
function export_list_of_folders(; url=get_url(), token=get_token(), folder_id=nothing,)
```

Export a list of files for all subfolders

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `folder_id`: folder_id of intended folder (default is the top-level directory of the File Repository)
