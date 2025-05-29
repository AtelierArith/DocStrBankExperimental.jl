```
function generate_next_record_name(; url=get_url(), token=get_token(),)
```

Generate the next record name

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
