```
ConfusionMatrix(pred::Vector{T}, truth::Vector{Bool}, τ::T) where {T <: Number}
```

スコアのベクトルと真の値のベクトル、さらに閾値を与えると、スコアをバイナリ予測に変換し、混同行列を返します。
