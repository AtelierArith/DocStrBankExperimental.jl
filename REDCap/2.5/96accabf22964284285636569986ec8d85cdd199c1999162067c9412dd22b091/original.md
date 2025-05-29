```
function import_user_DAG_assignment(; url=get_url(), token=get_token(), data, format=nothing, returnFormat=nothing,)
```

Switch the REDCap API user's current Data Access Group (DAG)

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `dag`: unique group name for the intended DAG
