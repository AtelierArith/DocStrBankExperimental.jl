```
alm2map(alm::Alm{ComplexF64, Array{Float64, 1}}, nside::Integer)
alm2map(alm::Alm{T, Array{T, 1}}, nside::Integer) where T
alm2map(alm::Array{Alm{ComplexF64, Array{ComplexF64, 1}},1}, nside::Integer)
alm2map(alms::Array{Alm{T, Array{T, 1}},1}, nside::Integer) where T
```

球面調和係数からマップを計算します。基盤となるSHTライブラリlibsharpはすべての計算をCdoublで行うため、すべての入力はFloat64に基づく型に変換されます。

# 引数

  * `alm`: 変換する球面調和係数。型が`Alm{T, Array{T, 1}}`の場合、スピン-0の球面調和変換を仮定します。`Alm`の配列が渡された場合、成分はT、E、B係数に対応すると仮定します。

# キーワード

  * `nside::Integer`: Healpix解像度パラメータ

# 戻り値

  * `HealpixMap{Float64, RingOrder, Array{Float64, 1}}`または`PolarizedHealpixMap{Float64, RingOrder, Array{Float64, 1}}`、入力のalmが型`Alm{T, Array{T, 1}}`または`Array{Alm{T, Array{T, 1}}}`のいずれかによって異なります。
