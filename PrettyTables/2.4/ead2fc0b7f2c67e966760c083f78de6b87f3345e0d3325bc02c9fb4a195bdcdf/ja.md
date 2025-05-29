```
hl_col(i::Number, crayon::Crayon) -> Highlighter
```

列 `i` 全体を `crayon` でハイライトします。

```
hl_col(cols::AbstractVector{Int}, crayon::Crayon) -> Highlighter
```

`cols` のすべての列を `crayon` でハイライトします。

!!! info
    これらの関数は、テキストバックエンドで使用するための `Highlighter` を返します。

