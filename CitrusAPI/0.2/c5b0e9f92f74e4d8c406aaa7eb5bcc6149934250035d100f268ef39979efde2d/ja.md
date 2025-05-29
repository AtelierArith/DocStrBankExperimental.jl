```
export_responses(client, survey_id, document_type; language=nothing, completion_status="all", heading_type="code", response_type="short", from=nothing, to=nothing, fields=nothing)
```

リモート調査から `survey_id` を `document_type` として base64 エンコードされた文字列として応答をエクスポートします。

参照: [https://api.limesurvey.org/classes/remotecontrol*handle.html#method*export_responses](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_export_responses)
