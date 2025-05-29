```
MvLocationLowRankScale(location, scale_diag, scale_factors, dist)
```

対角行列と二乗低ランク行列の形を持つ共分散を持つ変分ファミリー。ランクは `size(scale_factors, 2)` で与えられます。

一般的に、サンプリングパスが次のように表現できる任意の分布を表します：

```julia
  d = length(location)
  r = size(scale_factors, 2)
  u_diag = rand(dist, d)
  u_factors = rand(dist, r)
  z = scale_diag.*u_diag + scale_factors*u_factors + location
```
