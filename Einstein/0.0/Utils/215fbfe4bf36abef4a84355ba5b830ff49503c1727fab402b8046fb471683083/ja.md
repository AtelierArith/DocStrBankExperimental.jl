```
sws_eigen(::Type{TR}, s::Integer, c::Complex{TR}, m::Integer, l_max::Integer) where {TR<:AbstractFloat}
```

球面-楕円体分解行列の固有値と固有ベクトルを計算します。

# 引数

  * `TR`: 浮動小数点変換のための型
  * `s::Integer`: スピン
  * `c::Complex`: 楕円率パラメータ
  * `m::Integer`: 方位数
  * `l_max::Integer`: 最大角数

# 参考文献

  * [Cook:2014cta](@citet*)
  * [duetosymmetry/qnm](https://github.com/duetosymmetry/qnm)
