```
function import_user_role_assignments(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, data,)
```

Import role assignments to a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `data`: May be a String, a file name, or a data type such as NamedTuple or Dict. Available attributes are user*name, unique*role*name, and data*access_group.
  * `format`: the format of the `data` input parameter: `:csv`, `:json`, or `:xml` (default). If `data` is a String or a file name, this value must indicate the correct format. If `data` is a NamedTuple, Dict, or similar type, this value will determine what format will be used internally to pass on the data.
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
