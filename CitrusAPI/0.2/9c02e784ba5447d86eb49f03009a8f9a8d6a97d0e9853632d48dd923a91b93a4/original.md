```
import_survey(client, data, data_type; kwargs...)
import_survey(client, file; kwargs...)
```

Import a survey to a remote LimeSurvey server. `data` is a Base64 encoded string of the survey data. It can be derived from a valid `lss`, `csv`, `txt` or `lsa` file. The file type is specified by `data_type`.

A survey can also be imported directly froma valid `file`.

## Keyword arguments

  * `name`: The new survey name (default: `nothing`)
  * `survey_id`: The new survey id (default: `nothing`)

See also: [https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_survey](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_survey)
