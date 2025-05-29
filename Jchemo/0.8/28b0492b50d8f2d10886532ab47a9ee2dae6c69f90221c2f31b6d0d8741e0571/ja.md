```
pcasph(; kwargs...)
pcasph(X; kwargs...)
pcasph(X, weights::Weight; kwargs...)
pcasph!(X::Matrix, weights::Weight; kwargs...)
```

球面PCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 主成分 (PC) の数。
  * `scal` : ブール値。`true` の場合、`X` の各列はその未修正標準偏差でスケーリングされます。

球面PCA (Locantore et al. 1990, Maronna 2005, Daszykowski et al. 2007)。行列 `X` は、関数 `Jchemo.colmedspa` によって計算された空間中央値によって中心化されます。

## 参考文献

Daszykowski, M., Kaczmarek, K., Vander Heyden, Y., Walczak, B., 2007.  データ分析におけるロバスト統計 - レビュー。ケモメトリクスとインテリジェントラボラトリーシステム 85, 203-219. https://doi.org/10.1016/j.chemolab.2006.06.016

Locantore N., Marron J.S., Simpson D.G., Tripoli N., Zhang J.T., Cohen K.L. 機能データのためのロバスト主成分分析, Test 8 (1999) 1–7

Maronna, R., 2005. ロバストスケールに基づく主成分と直交回帰, Technometrics, 47:3, 264-273, DOI: 10.1198/004017005000000166

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "octane.jld2") 
@load db dat
@names dat
X = dat.X 
wlst = names(X)
wl = parse.(Float64, wlst)
n = nro(X)

nlv = 3
model = pcasph(; nlv)  
#model = pcasvd(; nlv) 
fit!(model, X)
@names model
@names model.fitm
@head T = model.fitm.T
## 同じ:
transf(model, X)

i = 1
plotxy(T[:, i], T[:, i + 1]; zeros = true, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1)).f
```
