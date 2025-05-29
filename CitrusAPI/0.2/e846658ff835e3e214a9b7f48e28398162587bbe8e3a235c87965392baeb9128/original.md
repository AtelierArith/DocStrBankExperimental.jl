```
import_group!(client, survey_id, data, data_type; name=nothing, description=nothing)
import_group!(client, survey_id, file; name=nothing, description=nothing)
```

Import a question group and add it to a remote survey with `survey_id`. `data` is a Base64 encoded string of the group data. It can be derived from a valid `lsg` or `csv` file which is specified by `data_type`.

A group can also be imported directly from a valid `lsg` or `csv` file by specifying `file`.

See also: [https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_group](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_group)
