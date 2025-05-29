```
hl_row(i::Number, crayon::Crayon) -> Highlighter
```

行 `i` 全体を `crayon` でハイライトします。

```
hl_row(rows::AbstractVector{Int}, crayon::Crayon) -> Highlighter
```

`rows` のすべての行を `crayon` でハイライトします。

!!! info
    これらの関数は、テキストバックエンドで使用するための `Highlighter` を返します。

