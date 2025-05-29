```
function export_file(; url=get_url(), token=get_token(), returnFormat=nothing, record=nothing, field=nothing, event=nothing, repeat_instance=nothing,)
```

Export a file from a record in a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `record`: record ID
  * `field`: name of field that contains file
  * `event`: unique event name (longitudinal projects)
  * `repeat_instance`: instance number of repeating event or instrument (where applicable, default is 1)
