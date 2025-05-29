```
scorecard(values; oncompletion::Bool=false, not_completed_msg::String="", which_attempt=:completed)
```

スコアカードを追加します

  * `values` は、`interval => message` のペアのコレクションです。以下を参照してください。デフォルトは、試行された質問の数と総質問数のうち、正解/試行された数を要約します。
  * `oncompletion` フラグは、すべての質問が試行された場合にのみメッセージを表示するように設定できます。設定されている場合、すべての質問が試行されていないときは、`not_completed_msg` メッセージが表示されます。
  * `which_percent` は `:correct` または `:attempted` のいずれかです。

インターバルは `(l,r)` として指定され、`0 <= l < r <= 100` であるか、*オプションで* `(l,r,interval_type)` として指定されます。ここで `interval_type` は文字列で、`"[]"`、`"[)"`、`"(]"`、または `"()"` のいずれかです。デフォルトのインターバルタイプは `"[)"` ですが、`r` が `100` の場合は `"[]"` になります。

メッセージは、正解/試行されたパーセントがインターバル内にあるときに表示されます。以下の値が存在する場合、置き換えられます：

  * `{{:total_questions}}` - 総質問数
  * `{{:correct}}` - 正解数
  * `{{:attempted}}` - 試行された質問数
  * `{{:total_attempts}}` – 試行回数。

メッセージにはMarkdown形式が含まれる場合があります。

例

```
vals = [(0,99)=>"頑張り続けてください",
          (99, 100) => "あなたは {{:correct}} **正解** のうち {{:total_questions}} の総 *質問* に対して正解しました"]
scorecard(vals)
```
