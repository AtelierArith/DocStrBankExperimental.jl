```
import_group!(client, survey_id, data, data_type; name=nothing, description=nothing)
import_group!(client, survey_id, file; name=nothing, description=nothing)
```

質問グループをインポートし、`survey_id`を持つリモート調査に追加します。`data`はグループデータのBase64エンコードされた文字列です。これは、`data_type`で指定された有効な`lsg`または`csv`ファイルから導出できます。

グループは、`file`を指定することで、有効な`lsg`または`csv`ファイルから直接インポートすることもできます。

参照: [https://api.limesurvey.org/classes/remotecontrol*handle.html#method*import_group](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_group)
