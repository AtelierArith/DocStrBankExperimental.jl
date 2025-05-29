```
function import_records(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, type=nothing, overwriteBehavior=nothing, forceAutoNumber=nothing, backgroundProcess=nothing, data, dateFormat=nothing, csvDelimiter=nothing, returnContent=nothing,)
```

Import records to a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, `:xml` (default), or `:odm`
  * `type`: `:flat` (default) or `:eav`
  * `overwriteBehavior`: overwrite data with blank values (by default, these are ignored)
  * `forceAutoNumber`: optionally determine record numbers automatically (these must be provided by default)
  * `backgroundProcess`: set to true for large uploads
  * `data`: May be a String, a file name, or a data type such as NamedTuple or Dict
  * `format`: the format of the `data` input parameter: `:csv`, `:json`, or `:xml` (default). If `data` is a String or a file name, this value must indicate the correct format. If `data` is a NamedTuple, Dict, or similar type, this value will determine what format will be used internally to pass on the data.
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `dateFormat`: `:MDY`, `:DMY`, or `:YMD` (default)
  * `csvDelimiter`: ',' (default), 'tab', ';', '|', or '^'
  * `returnContent`: sets the return value (`:count` (default, `:lds`, or `:auto_lds`)
