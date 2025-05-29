```
function delete_user_roles(; url=get_url(), token=get_token(), roles,)
```

Delete roles from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `roles`: unique role names (can be scalar or vector)
