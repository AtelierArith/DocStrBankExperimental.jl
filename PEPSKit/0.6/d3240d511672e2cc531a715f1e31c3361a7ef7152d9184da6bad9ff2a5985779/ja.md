```
InfiniteWeightPEPS(vertices::Matrix{T}, weight_mats::Matrix{E}...) where {T<:PEPSTensor,E<:PEPSWeight}
```

ユニットセル内のすべての位置におけるボンドの各タイプに対する重みの行列と、頂点テンソルの行列からInfiniteWeightPEPSを作成します。
