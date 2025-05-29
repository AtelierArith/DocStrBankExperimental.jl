```
map2alm(map::HealpixMap{Float64, RingOrder, AA};
    lmax=nothing, mmax=nothing, niter::Integer=3)
map2alm(m::HealpixMap{T, RingOrder, AA}; lmax=nothing, mmax=nothing,
    niter::Integer=3) where {T <: Real, AA <: AbstractArray{T, 1} }
```

地図の球面調和係数を計算します。精度を高めるために、非ゼロの `niter` を渡すことで変換の反復回数を増やすことができます。基盤となるSHTライブラリlibsharpは、すべての計算を`Cdouble`型を使用して行うため、すべての入力はFloat64に基づく型に変換されます。

# 引数

  * `map`: 球面調和に分解する地図。`HealpixMap{T, RingOrder, AA}`型（スカラー地図）または`PolarizedHealpixMap{T, RingOrder, AA}`型（偏光地図）である必要があります。

# キーワード

  * `lmax::Integer`: 最大ℓ係数。指定されていない場合は3*nside-1がデフォルトになります。
  * `mmax::Integer`: 最大m係数
  * `niter::Integer`: 精度を高めるためのSHT反復回数。デフォルトは3です。

# 戻り値

  * `Alm{ComplexF64, Array{ComplexF64, 1}}`: 地図に対応する球面調和係数
