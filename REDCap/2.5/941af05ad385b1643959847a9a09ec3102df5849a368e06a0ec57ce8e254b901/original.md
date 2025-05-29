```
function delete_records(; url=get_url(), token=get_token(), records, arm=nothing, instrument=nothing, event=nothing, repeat_instance=nothing,)
```

Delete records from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `records`: record names (can be scalar or vector)
  * `arm`: optionlly limit deletions to this arm number
  * `instrument`: optionlly limit deletions to this unique instrument name
  * `event`: optionlly limit deletions to this unique event name (required for longitudinal projects, otherwise unavailable)
  * `repeat_instance`: optionlly limit deletions to this repeating instrument or event
  * `delete_logging`: if true, delete logging activity for deleted record (default is false)
