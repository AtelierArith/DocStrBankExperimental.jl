```
function export_events(; url=get_url(), token=get_token(), format=nothing, arms=nothing,)
```

Export Events from a longitudinal REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `arms`: study arms from which to pull events (all are inclued by default)
