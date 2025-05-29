```
function export_repeating_instruments_and_events(; url=get_url(), token=get_token(), format=nothing,)
```

Export a list of repeating instruments and events for a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
