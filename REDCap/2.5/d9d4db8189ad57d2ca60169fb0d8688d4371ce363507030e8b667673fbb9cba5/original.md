```
function export_survey_participants(; url=get_url(), token=get_token(), format=nothing, returnFormat=nothing, instrument=nothing, event=nothing, repeat_instance=nothing,)
```

Export a list of survey participants

# Named arguments

  * `url`: (read from `ENV["REDCAP_API_URL"]` by default)
  * `token`: an API token specific to the REDCap project and username (read from `ENV["REDCAP_API_TOKEN"]` by default)
  * `returnFormat`: the desired output format: `:csv`, `:json`, or `:xml` (default)
  * `instrument`: the instrument's name (must be enabled as a survey)
  * `event`: the unique event name (longitudinal projects only)
