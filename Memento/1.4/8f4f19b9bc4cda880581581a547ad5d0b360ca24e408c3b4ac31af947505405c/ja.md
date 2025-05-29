```
Escalator(fmt=DefaultFormatter(); level="warn", levels=nothing)
```

特定の `level` を超えるログをすべてエスカレートし、`EscalationError` をスローします。

# 引数

  * `fmt::Formatter`: `Record` をエラーメッセージの `Strings` に変換するためのフォーマッタ

# キーワード引数

  * `level`: エラーを発生させるための閾値レベル、そうでなければこれは何もしません
  * `levels`: デフォルト以外のレベルを考慮する場合の代替レベル辞書
