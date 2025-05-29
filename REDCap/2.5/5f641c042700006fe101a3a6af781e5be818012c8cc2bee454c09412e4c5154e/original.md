```
function export_arms(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, arms=nothing,)
```

Export a REDCap project's study arms

# Notes

If no value is provided for `arms`, all study arms are returned.

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `arms`: names of study arms (can be scalar or vector)
