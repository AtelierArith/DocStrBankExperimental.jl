```
function rename_record(; url=get_url(), token=get_token(), record, new_record_name, arm=nothing,)
```

Rename a record

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `record`: current record name
  * `new_record_name`: new record name
  * `arm`: optionally limit renaming to this arm number
