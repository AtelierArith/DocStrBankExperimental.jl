```
residuals(radec::AbstractVector{RadecMPC{T}}, w8s::AbstractVector{Tuple{T, T}},
    bias::AbstractVector{Tuple{T, T}}; xva::AstEph,
    kwargs...) where {AstEph, T <: Real}
```

光学天体測定 `radec` の観測値と計算値の残差を計算します。地球の姿勢、LOD、および極運動による修正はデフォルトで計算されます。

[`OpticalResidual`](@ref) および [`compute_radec`](@ref) も参照してください。

## 引数

  * `radec::AbstractVector{RadecMPC{T}}`: 光学天体測定。
  * `w8s::AbstractVector{Tuple{T, T}}`: 統計的重み。
  * `bias::AbstractVector{Tuple{T, T}}`: デバイアス修正。

## キーワード引数

  * `niter::Int`: 光到達時間解の反復回数 (デフォルト: `5`)。
  * `xve::EarthEph`: 地球のエフェメリス (デフォルト: `earthposvel`)。
  * `xvs::SunEph`: 太陽のエフェメリス (デフォルト: `sunposvel`)。
  * `xva::AstEph`: 小惑星のエフェメリス。

すべてのエフェメリスは [J2000 からの秒数] を受け取り、[バリセントリック位置 (km) と速度 (km/sec)] を返さなければなりません。
