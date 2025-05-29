```
logsoftmax(x; dims = 1)
```

より数値的に安定した方法でソフトマックスの対数を計算します。直接 `log.(softmax(xs))` を取るよりも一般的に使用されます。交差エントロピー損失を計算する際に一般的に使用されます。

次のように意味的に等価です：

```
logsoftmax(x; dims = 1) = x .- log.(sum(exp.(x), dims = dims))
```

詳細は [`softmax`](@ref) を参照してください。
