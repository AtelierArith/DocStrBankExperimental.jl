```
ScalarColumn(n, header, ::Type{R}[, signed=false]) where {R<:Real}
```

コールバック関数 `n` のための [`ScalarColumn`](@ref) を構築します。フォーマットは、`R` が整数かどうか、また符号付きかどうかに応じて自動的に生成されます。
