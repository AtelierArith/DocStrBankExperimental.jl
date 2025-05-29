```
compute_receptor_emis(srm, source_idx(s), layer_idx(s), val(s)) -> receptor_emis::Vector
```

`srm`から各受容体での排出量を計算します。`source_idx`および`layer_idx`で指定された各ソースに対応し、これらは`val(s)`に関連しています。

```
compute_receptor_emis(srm, source_emis::Matrix) -> receptor_emis::Vector
```

`srm`から各受容体での排出量を計算します。`source_emis`は、各グリッドセルおよび層での年間平均排出率を含む`NSR x 3`行列で、単位はマイクログラム毎秒です。

`srm`は以下のいずれかのタイプであることができます：

  * `Array{Float64, 3}` - [`SRM`](@ref)によって返される
  * [`SparseSRM`](@ref)
  * `String` - pm排出タイプ ∈ `("PrimaryPM25", "SOA", "pNO3", "pSO4", "pNH4")`
