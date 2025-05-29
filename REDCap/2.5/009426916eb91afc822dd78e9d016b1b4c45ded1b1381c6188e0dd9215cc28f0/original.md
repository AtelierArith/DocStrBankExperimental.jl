```
function delete_DAGs(; url=get_url(), token=get_token(), dags)
```

Delete Data Access Groups (DAGs) from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `dags`: group names (can be scalar or vector)
