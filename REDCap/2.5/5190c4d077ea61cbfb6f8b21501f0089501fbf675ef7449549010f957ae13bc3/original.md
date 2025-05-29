```
function export_logging(; url=get_url(), token=get_token(), format=nothing, logtype=nothing, user=nothing, record=nothing, dag=nothing, beginTime=nothing, endTime=nothing,)
```

Export mappings of data collection instruments onto designated Events for a longitudinal REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `logtype`: optionally limit output to an event type (export, manage, user, record, record*add, record*edit, record*delete, lock*record, page_view)
  * `user`: optionally limit output to a specific user
  * `record`: optionally limit output to a specific record
  * `dag`: optionally limit output to a specific Data Access Group (DAG)
  * `beginTime`: optionally limit output to events logged after a given datetime
  * `endTime`: optionally limit output to events logged before a given datetime
