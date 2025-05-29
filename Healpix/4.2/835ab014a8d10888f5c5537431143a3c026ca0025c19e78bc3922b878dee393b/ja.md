```
alm2map!(alm::Alm{ComplexF64, Array{ComplexF64, 1}}, map::HealpixMap{Float64, RingOrder, Array{Float64, 1}})
alm2map!(alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1}, map::PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}})
```

この関数は、地図に球面調和変換を実行し、結果を渡された `alm` オブジェクトに配置します。この関数は、インプレースで行われるため、Float64から派生した型を必要とします。

# 引数

  * `alm::Alm{ComplexF64, Array{ComplexF64, 1}}`: 球面調和変換を実行するための球面調和係数。
  * `map`: 結果を含む地図。これは `HealpixMap{Float64, RingOrder, Array{Float64, 1}}` 型（スカラー地図）または `PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}`（偏光地図）であることができます。
