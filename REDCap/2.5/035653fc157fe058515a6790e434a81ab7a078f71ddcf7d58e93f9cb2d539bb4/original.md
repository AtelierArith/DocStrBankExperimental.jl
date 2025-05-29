```
function export_records(; url=get_url(), token=get_token(), format=nothing, type=nothing, records=nothing, fields=nothing, forms=nothing, events=nothing, rawOrLabel=nothing, rawOrLabelHeaders=nothing, exportCheckboxLabel=nothing, exportSurveyFields=nothing, exportDataAccessGroups=nothing, filterLogic=nothing, dateRangeBegin=nothing, dateRangeEnd=nothing, csvDelimiter=nothing, decimalCharacter=nothing, exportBlankForGrayFormStatus=nothing)
```

Export records from a REDCap project

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `format`: the desired output format: `:csv`, `:json`, `:xml` (default), or `:odm`
  * `type`: `:flat` (default) or `:eav`
  * `records`: optionally limit exports to specific records (can be scalar or vector)
  * `fields`: optionally limit exports to specific field names (can be scalar or vector)
  * `forms`: optionally limit exports to specific form names (can be scalar or vector)
  * `events`: (longitudinal projects only) optionally limit exports to specific unique event names (can be scalar or vector)
  * `rawOrLabel`: `:raw` (default, export raw coded values) or `:label` (export labels)
  * `rawOrLabelHeaders`: (for `:flat` type, `:csv` format only) raw or label CSV headers
  * `exportCheckboxLabel`: toggle format of checkbox field values (false by default)
  * `exportSurveyFields`: optionally export survey identifier and timestamp fields (false by default)
  * `exportDataAccessGroups`: optionally export the "redcap*data*access_group" field (false by default)
  * `filterLogic` : optionally filter records based on a logic string
  * `dateRangeBegin`: optionally limit output to records created or modified after a given datetime
  * `dateRangeEnd`: optionally limit output to records created or modified before a given datetime
  * `csvDelimiter`: ',' (default), 'tab', ';', '|', or '^'
  * `decimalCharacter`: enforce ',' or '.'  format (empty by default)
  * `exportBlankForGrayFormStatus`: optionally export blank values for instrument complete status fields with a gray status icon
