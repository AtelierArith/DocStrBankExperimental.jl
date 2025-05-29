```
function export_PDF(; url=get_url(), token=get_token(), format=nothing, record=nothing, event=nothing, instrument=nothing, repeat_instance=nothing, allRecords=nothing, compactDisplay=nothing,)
```

Export PDF of Data Collection Instruments

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `record: record ID (default is a PDF with no data)
  * `event`: unique event name for a longitudinal project
  * `instrument`: unique instrument name
  * `repeat_instance`: repeat instance number for projects with repeating instruments/events
  * `allRecords`: if passed with any value, all records are exported
  * `compactDisplay`: if true, excludes empty fields and unselected options (default is false)
