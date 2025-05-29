```
KeplerSolver(M::T, e::Number; tol::Float64=10 * eps(T)) where {T<:Number}
```

軌道の平均異常と離心率から真異常を解決します。

# 引数

-`M::Number`: 軌道の平均異常 [ラジアン]. -`e::Number`: 軌道の離心率.

# キーワード引数

-`tol::Float64`: ケプラーソルバーの収束許容値. [デフォルト=10*eps(T)]

# 戻り値

-`f::Number``: 軌道の真異常 [ラジアン]
