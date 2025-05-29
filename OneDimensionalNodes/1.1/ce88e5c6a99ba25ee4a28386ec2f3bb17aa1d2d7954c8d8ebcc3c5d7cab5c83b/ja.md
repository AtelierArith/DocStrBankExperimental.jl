```
spectralinterpolation(r, s, w=barycentricweights(r))
```

点 `r` で定義された多項式の補間行列を作成し、関連するバリセントリック重み `w` を用いて点 `s` で評価します。`barycentricweights` および `spectralderivative` も参照してください。

# 例

レジェンドル–ガウス–ロバット点で多項式を評価する補間行列を、等間隔のグリッドで作成します。

```jldoctest
julia> x, _ = legendregausslobatto(4);
julia> y = collect(-1:0.4:1);
julia> spectralinterpolation(x,y)
6×4 Matrix{Float64}:
  1.0           0.0           0.0           0.0
  0.16          0.936656     -0.136656      0.04
 -0.12          0.868328      0.331672     -0.08
 -0.08          0.331672      0.868328     -0.12
  0.04         -0.136656      0.936656      0.16
 -1.11022e-16   3.43078e-16  -8.98189e-16   1.0
```

# 参考文献

Jean-Paul Berrut & Lloyd N. Trefethen, "Barycentric Lagrange Interpolation",   SIAM Review 46 (2004), pp. 501-517.   [https://doi.org/10.1137/S0036144502417715](https://doi.org/10.1137/S0036144502417715)
