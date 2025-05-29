```
function import_events(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, data=nothing, override=nothing,)
```

Import new Events to a longitudinal REDCap project, or update the attributes of existing Events

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `data`: May be a String, a file name, or a data type such as NamedTuple or Dict
  * `override`: if true, all existing Events are erased; if false (default), existing Events can only be updated
  * `format`: the format of the `data` input parameter: `:csv`, `:json`, or `:xml` (default). If `data` is a String or a file name, this value must indicate the correct format. If `data` is a NamedTuple, Dict, or similar type, this value will determine what format will be used internally to pass on the data.
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
