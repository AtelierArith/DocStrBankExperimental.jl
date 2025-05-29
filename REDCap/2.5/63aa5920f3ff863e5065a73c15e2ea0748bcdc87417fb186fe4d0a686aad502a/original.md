```
function delete_events(; url=get_url(), token=get_token(), events=nothing,)
```

Delete Events from a longitudinal REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `events`: unique event names (can be scalar or vector)
