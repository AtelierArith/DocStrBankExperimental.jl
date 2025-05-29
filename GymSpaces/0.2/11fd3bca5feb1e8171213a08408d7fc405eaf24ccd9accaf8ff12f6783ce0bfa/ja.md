```
Box(low::Number, high::Number, shape::Union{Tuple, Array{<:Integer, 1}}, dtype::Union{DataType, Nothing}=nothing; seed::Int=42)
```

R^nのボックスで、`low`と`high`のベクトルの低値と高値を持ち、形状は`shape`です。サンプリング用のオプション入力`seed`。

例 Box(-1.0, 1.0, (3,4)) # lowとhighはスカラーで、形状が提供されています。
