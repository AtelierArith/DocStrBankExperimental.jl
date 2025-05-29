```
neigs_snd, neigs_rcv = assembly_neighbors(index_partition;kwargs...)
```

分散ベクトルの組み立てにおいて、送信および受信データの隣接部分のIDをそれぞれ返します。これは、インデックスパーティション `index_partition` に定義されています。 `kwargs` は、送信側から受信側の隣接を見つけるために [`ExchangeGraph`](@ref) に委任されます。
