```
hl_cell(i::Number, j::Number, crayon::Crayon) -> Highlighter
```

セル `(i,j)` を `crayon` でハイライトします。

```
hl_cell(cells::AbstractVector{NTuple(2,Int)}, crayon::Crayon) -> Highlighter
```

すべての `cells` を `crayon` でハイライトします。

!!! info
    これらの関数は、テキストバックエンドで使用するための `Highlighter` を返します。

