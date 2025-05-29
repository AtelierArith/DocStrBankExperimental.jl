```
parse_entry(entry::String; parser::Symbol = :BibTeX, check = :error)
```

文字列エントリを解析します。デフォルトはBibTeX形式です。他のオプションはまだ利用できません（CSL-JSONが近日中に登場予定）。

書誌形式にフォーマットルールがある場合（例えば`:BibTeX`）、`check`キーワード引数は`:none`（または`nothing`）、`:warn`、または`:error`に設定できます。
