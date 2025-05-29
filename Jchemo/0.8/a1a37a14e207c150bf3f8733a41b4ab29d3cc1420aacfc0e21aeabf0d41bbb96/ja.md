```
outeucl(X; kwargs...)
outeucl!(X::Matrix; kwargs...)
```

中心からのユークリッド距離に基づいて外れ値度を計算します。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `scal` : ブール値。`true` の場合、外れ値度を計算する前に、`X` の各列がそのMADでスケーリングされます。

外れ値度は、観測値（`X` の行）とデータのロバストな中心の推定値（この関数では空間的中央値）との間のユークリッド距離によって計算されます。このような外れ値度は、例えば、Serneels et al. 2005 のロバストPLSRアルゴリズムで使用されました（PRM）。

## 参考文献

Serneels, S., Croux, C., Filzmoser, V., Van Espen, V.J., 2005. Partial robust M-regression.  Chemometrics and Intelligent Laboratory Systems 79, 55-64.  https://doi.org/10.1016/j.chemolab.2005.04.007

## 例

```julia
using Jchemo, CairoMakie
n = 300 ; p = 700 ; m = 80
ntot = n + m
X1 = randn(n, p)
X2 = randn(m, p) .+ rand(1:3, p)'
X = vcat(X1, X2)

scal = false
#scal = true
res = outeucl(X; scal) ;
@names res
res.d    # 外れ値度 
plotxy(1:ntot, res.d).f
```
