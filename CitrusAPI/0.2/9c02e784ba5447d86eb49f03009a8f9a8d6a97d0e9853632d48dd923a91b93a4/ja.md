```
import_survey(client, data, data_type; kwargs...)
import_survey(client, file; kwargs...)
```

リモートLimeSurveyサーバーに調査をインポートします。`data`は調査データのBase64エンコードされた文字列です。有効な`lss`、`csv`、`txt`または`lsa`ファイルから派生させることができます。ファイルタイプは`data_type`で指定されます。

調査は、有効な`file`から直接インポートすることもできます。

## キーワード引数

  * `name`: 新しい調査名（デフォルト: `nothing`）
  * `survey_id`: 新しい調査ID（デフォルト: `nothing`）

参照: [https://api.limesurvey.org/classes/remotecontrol*handle.html#method*import_survey](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_survey)
