```
mcc(C::Vector{<:ConfusionMatrix}, full::Bool=false)
```

混同行列のベクトルを使用した `mcc` のバージョン。平均を返し、第二引数が `true` の場合は、第二引数が CI であるタプルを返します。
