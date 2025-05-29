```
hl = passfail_highlighter(df, c=crayon"bold red")
```

デフォルトで失敗を太字の赤で色付けするPrettyTablesハイライターです。

### 入力引数

  * `df::DataFrame` ハイライターが適用されるデータフレーム。 `df` は `id` 列を持っている必要があります。

`df` に `:status` プロパティがある場合、ハイライターは `df.status` が失敗を示す行に適用されます。失敗は `:first_order` または `:unbounded` とは異なる任意のステータスです。
