```
train!(wnn::WNN{S, T}, x::S, y::Vector{Bool}) where {S, T}
```

クラス `x` とサンプル `y` の単一ペアでモデルをトレーニングします。
