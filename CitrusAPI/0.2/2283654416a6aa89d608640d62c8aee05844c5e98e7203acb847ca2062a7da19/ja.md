```
remind_participants(client, survey_id; kwargs...)
```

`survey_id`を持つリモート調査の参加者にリマインダーを送信します。

## キーワード引数

  * `min_days_between`: 最後のリマインダーからの日数 (デフォルト: `nothing`)
  * `max_reminders`: 最大リマインダー数
  * `token_ids`: リマインドする参加者のID (デフォルト: false)

参照: [https://api.limesurvey.org/classes/remotecontrol*handle.html#method*remind_participants](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_remind_participants)
