```
function export_project_XML(; url=get_url(), token=get_token(), returnFormat=nothing, returnMetadataOnly=nothing, records=nothing, fields=nothing, events=nothing, exportSurveyFields=nothing, exportDataAccessGroups=nothing, filterLogic=nothing, exportFiles=nothing,)
```

Export an entire REDCap project as an XML project file, which can be used to create a new project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `records`: optionally limit output to these record names (can be scalar or vector)
  * `fields`: optionally limit output to these field names (can be scalar or vector)
  * `events`: optionally limit output to these unique event names (can be scalar or vector)
  * `returnMetadataOnly`: optionally return metadata with no data (default is false)
  * `exportSurveyFields`: optionally export survey identifier and timestamp fields (default is false)
  * `exportDataAccessGroups`: optionally export `redcap_data_access_group` field (default is false)
  * `exportFiles`: optionally include contents of File Upload and Signature fields (default is false)
  * `filterLogic`: logic string for filtering records
