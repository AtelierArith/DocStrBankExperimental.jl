```
branches(path::EinExpr[, i])
```

`path`の非終端ブランチを返します。これは収束ステップの中間テンソル結果に対応します。`i`が指定されている場合、$i$-番目の`EinExpr`のみを返します。

関連情報: [`leaves`](@ref), [`Branches`](@ref).
