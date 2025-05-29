```
function delete_users(; url=get_url(), token=get_token(), users)
```

Delete users from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `users`: user names (can be scalar or vector)
