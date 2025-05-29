```
parse_file(path::String, parser::Symbol = :BibTeX; check=:error)
```

文献ファイルを解析します。デフォルトはBibTeX形式です。他のオプションとしては、CFF（CSL-JSONは近日中に対応予定）があります。フォーマットルールを持つ文献形式（例えば`:BibTeX`）の場合、`check`キーワード引数は`:none`（または`nothing`）、`:warn`、または`:error`に設定できます。
