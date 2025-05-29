```
outstah(X, V; kwargs...)
outstah!(X::Matrix, V::Matrix; kwargs...)
```

スタヘル-ドノホ外れ値度を計算します。

  * `X` : Xデータ (n, p)。
  * `V` : 投影追求の方向を表す投影行列 (p, nlv)。

キーワード引数:

  * `scal` : ブール値。`true` の場合、外れ値度を計算する前に、`X` の各列がそのMADでスケーリングされます。

外れ値度の測定に関する詳細は、Maronna と Yohai 1995 を参照してください。

投影追求アプローチが使用されます：投影行列 `V` (p, nlv)（一般的にはランダムに構築される）を与えられた場合、観測値（`X` の行）は `nlv` の方向に投影され、これらの投影から各観測値のスタヘル-ドノホ外れ値度が計算されます。

## 参考文献

Maronna, R.A., Yohai, V.J., 1995. The Behavior of the Stahel-Donoho Robust Multivariate  Estimator. Journal of the American Statistical Association 90, 330–341.  https://doi.org/10.1080/01621459.1995.10476517

## 例

```julia
using Jchemo, CairoMakie

n = 300 ; p = 700 ; m = 80
ntot = n + m
X1 = randn(n, p)
X2 = randn(m, p) .+ rand(1:3, p)'
X = vcat(X1, X2)

nlv = 100
V = rand(0:1, p, nlv)
scal = false
#scal = true
res = outstah(X, V; scal) ;
@names res
res.d    # 外れ値度 
plotxy(1:ntot, res.d).f
```
