```
pv2kep(xas::Vector{U}; μ::T = μ_S, jd::T = JD_J2000,
       frame::Symbol = :equatorial) where {T <: Real, U <: Number}
```

状態ベクトル `xas` を持つ NEO の軌道要素を計算します。`OsculatingElements` オブジェクトを返します。

関連情報としては、[`equatorial2ecliptic`](@ref)、[`eccentricity`](@ref)、[`semimajoraxis`](@ref)、[`timeperipass`](@ref)、[`longascnode`](@ref)、[`argperi`](@ref) および [`inclination`](@ref) があります。

# 引数

  * `xas::Vector{U}`: 小惑星の状態ベクトル `[x, y, z, v_x, v_y, v_z]`。
  * `μ_S::T`: 中心天体（太陽）の質量パラメータ。
  * `jd::T`: ユリウス日での基準軌道エポック。
  * `frame::Symbol`: 参照平面（`:equatorial` または `:ecliptic`）。
