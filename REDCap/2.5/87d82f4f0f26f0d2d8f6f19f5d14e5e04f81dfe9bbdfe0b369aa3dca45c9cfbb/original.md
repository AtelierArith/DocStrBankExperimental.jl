```
function import_arms(; url=get_url(), token=get_token(), format=nothing, data, returnFormat=nothing, override=nothing,)
```

Import new study arms to a REDCap project, or rename existing arms

# Notes

Deleting a study arm deletes any included records and data.

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `arms`: names of study arms (can be scalar or vector)
  * `override`: if true, all existing arms are erased; if false (default), existing arms can only be renamed
  * `data`: May be a String, a file name, or a data type such as NamedTuple or Dict
  * `format`: the format of the `data` input parameter: `:csv`, `:json`, or `:xml` (default). If `data` is a String or a file name, this value must indicate the correct format. If `data` is a NamedTuple, Dict, or similar type, this value will determine what format will be used internally to pass on the data.
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
