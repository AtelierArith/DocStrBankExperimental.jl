```
import_question!(client, survey_id, group_id, data, data_type; kwargs...)
import_question!(client, survey_id, group_id, file; kwargs...)
```

質問をインポートし、`survey_id`を持つリモート調査内の`group_id`によって質問グループに追加します。`data`は質問データのBase64エンコードされた文字列です。有効な`lsq`または`csv`ファイルから導出できます。ファイルタイプは`data_type`によって指定されます。

質問は、`file`を指定することによって、有効な`lsq`または`csv`ファイルから直接インポートすることもできます。

## キーワード引数

  * `mandatory`: 質問を必須としてマークする（デフォルト: `false`）
  * `title`: 質問のタイトル（デフォルト: `nothing`）
  * `text`: 質問の内容（デフォルト: `nothing`）
  * `help`: 質問のヘルプテキスト（デフォルト: `nothing`）

詳細については、[https://api.limesurvey.org/classes/remotecontrol*handle.html#method*import_question](https://api.limesurvey.org/classes/remotecontrol_handle.html#method_import_question)を参照してください。
