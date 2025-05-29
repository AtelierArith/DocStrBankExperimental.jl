```
function delete_arms(; url=get_url(), token=get_token(), arms,)
```

Delete study arms from a REDCap project

# Notes

If no value is provided for `arms`, all study arms are returned. Deleting a study arm deletes any included records and data.

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `arms`: names of study arms (can be scalar or vector)
