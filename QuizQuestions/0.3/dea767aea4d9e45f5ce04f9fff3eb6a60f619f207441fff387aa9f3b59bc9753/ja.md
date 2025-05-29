```
fillblankq(question answer::Regex; placeholder=nothing, [label, hint, explanation])
fillblankq(question, choices, answer; keep_order=false,[label, hint, explanation])
fillblankq(question, val, atol=0; placeholder=nothing, [label, hint, explanation])
```

空欄を選択、数値、または文字列として、正規表現によって採点される填空問題を提示します。

  * `question`: 文字列。空欄を示すために `____`（4つ以上のアンダースコア）を使用します。

`stringq`、`radioq`、および `numericq` からの他の引数

## 例

```
question = "The quick brown fox jumped over the ____ dog"
fillblankq(question, r"lazy")
fillblankq(question, ("lazy", "brown", "sleeping"), 1)
fillblankq("____ ``+ 2  = 4``", 2)
```
