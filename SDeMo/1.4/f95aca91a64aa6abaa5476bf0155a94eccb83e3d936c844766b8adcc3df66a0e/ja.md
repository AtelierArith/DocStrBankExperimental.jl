```
balancedaccuracy(C::Vector{<:ConfusionMatrix}, full::Bool=false)
```

混同行列のベクトルを使用した `balancedaccuracy` のバージョン。平均を返し、第二引数が `true` の場合は、第二引数がCIであるタプルを返します。
