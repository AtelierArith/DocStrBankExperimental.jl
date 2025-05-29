```
remind_participants(client, survey_id; kwargs...)
```

Send reminders to participants of the remote survey with `survey_id`.

## Keyword arguments

  * `min_days_between`: Number of days from last reminder (default: `nothing`)
  * `max_reminders`: Maximum number of reminders
  * `token_ids`: Ids of the participants to remind (default: false)

See also: [https://api.limesurvey.org/classes/remotecontrol_handle.html#method_remind_participants](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_remind_participants)
