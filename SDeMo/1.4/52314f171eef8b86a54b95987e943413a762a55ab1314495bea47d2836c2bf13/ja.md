```
ConfusionMatrix(pred::Vector{T}, truth::Vector{Bool}) where {T <: Number}
```

スコアのベクトルと真実のベクトルを与えると、スコアが確率であり、しきい値が1/2であるという仮定の下で混同行列を返します。
