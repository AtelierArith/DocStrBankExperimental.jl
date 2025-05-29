```
log_text(logger::TBLogger, name::String, text::Any; step=step(logger))
```

名前 `name` でステップ `step` にテキストをログします

  * text: テキストが 2-D または 3-D の `Array` の場合、テーブルまたはリストとしてレンダリングされます。それ以外のデータは文字列として表されます。
