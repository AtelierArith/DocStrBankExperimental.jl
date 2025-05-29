```
import_question!(client, survey_id, group_id, data, data_type; kwargs...)
import_question!(client, survey_id, group_id, file; kwargs...)
```

Import a question and add it to a question group by `group_id` within a remote survey with `survey_id`. `data` is a Base64 encoded string of the question data. It can be derived from a valid `lsq` or `csv` file. The file type is specified by `data_type`.

A question can also be imported directly from a valid `lsq` or `csv` file by specifying `file`.

## Keyword arguments

  * `mandatory`: Mark the question as mandatory (default: `false`)
  * `title`: The question title (default: `nothing`)
  * `text`: The question content (default: `nothing`)
  * `help`: The question help text (default: `nothing`)

See also: [https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_question](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_question)
