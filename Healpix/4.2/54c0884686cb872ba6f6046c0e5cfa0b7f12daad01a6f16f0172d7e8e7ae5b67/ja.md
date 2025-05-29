```
adjoint_alm2map!(map::HealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Alm{ComplexF64, Array{ComplexF64, 1}})
adjoint_alm2map!(map::PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}, alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1})
```

この関数は、地図に対して球面調和変換 Yᵀ を実行し、結果を渡された `alm` オブジェクトに配置します。この関数は、インプレースで行われるため、Float64 から派生した型を必要とします。

# 引数

  * `map`: 球面調和に分解される必要がある地図。これは `HealpixMap{Float64, RingOrder}` 型（スカラー地図）または `PolarizedHealpixMap{Float64, RingOrder}` 型（偏光地図）であることができます。
  * `alm::Alm{ComplexF64, Array{ComplexF64, 1}}`: 書き込む球面調和係数です。
