```julia
struct SubperiodicGroup{D, P} <: Crystalline.AbstractGroup{D, Crystalline.SymOperation{D}}
```

  * `num::Int64`
  * `operations::Array{Crystalline.SymOperation{D}, 1} where D`

埋め込み次元 `D` と周期次元 `P` の部分周期群。

フィールド:

  * `operations`: 有限因子群 $G/T$ の `SymOperation`、ここで $G$ は部分周期群であり、$T$ は関連する格子の平行移動群です。
  * `num`: 国際結晶学表、ボリューム E に従った群の標準番号。
