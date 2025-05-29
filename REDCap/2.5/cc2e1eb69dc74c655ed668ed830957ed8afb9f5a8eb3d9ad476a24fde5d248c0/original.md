```
function export_file_from_file_repository(; url=get_url(), token=get_token(), doc_id=nothing,
```

Export a File from the File Repository

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `doc_id`: the file's doc_id
