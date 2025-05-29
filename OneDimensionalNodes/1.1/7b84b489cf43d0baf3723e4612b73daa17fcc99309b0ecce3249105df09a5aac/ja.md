```
spectralderivative(r, w=barycentricweights(r))
```

点 `r` で定義された多項式のための、`r` と同様の型の微分行列を作成します。関連するバリセントリック重み `w` については、`barycentricweights` および `spectralinterpolation` を参照してください。

# 例

レジェンドル–ガウス–ロバット点の微分行列を作成します

```jldoctest
julia> x, _ = legendregausslobatto(4);
julia> spectralderivative(x)
4×4 Matrix{Float64}:
 -3.0        4.04508      -1.54508       0.5
 -0.809017   7.77156e-16   1.11803      -0.309017
  0.309017  -1.11803      -1.55431e-15   0.809017
 -0.5        1.54508      -4.04508       3.0
```

# 参考文献

Jean-Paul Berrut & Lloyd N. Trefethen, "Barycentric Lagrange Interpolation",   SIAM Review 46 (2004), pp. 501-517.   [https://doi.org/10.1137/S0036144502417715](https://doi.org/10.1137/S0036144502417715)
