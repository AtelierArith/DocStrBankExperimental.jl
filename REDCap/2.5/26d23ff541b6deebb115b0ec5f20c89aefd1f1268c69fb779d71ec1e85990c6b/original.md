```
function export_metadata(; url=get_url(), token=get_token(), format=nothing, fields=nothing, forms=nothing,)
```

Export metadata (Data Dictionary) from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `fields`: field names (can be scalar or vector). By default, all fields are pulled.
  * `fields`: unique form names for data collection instruments (can be scalar or vector). By default, all fields are pulled.
