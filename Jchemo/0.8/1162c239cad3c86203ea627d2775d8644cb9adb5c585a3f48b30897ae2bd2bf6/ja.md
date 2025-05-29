```
pcaout(; kwargs...)
pcaout(X; kwargs...)
pcaout(X, weights::Weight; kwargs...)
pcaout!(X::Matrix, weights::Weight; kwargs...)
```

外れ値性を用いたロバストPCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。`Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `prm` : 各外れ値性指標に対して除去されるデータの割合 (外れ値のハードリジェクション)。
  * `scal` : ブール値。`true`の場合、外れ値性を計算する際に`X`の各列はそのMADでスケーリングされ、重み付きPCAを計算する際にはその未修正標準偏差でスケーリングされます。

外れ値性指標と重み付きPCA (WPCA) を組み合わせたロバストPCA。

目的は、潜在的に悪いレバレッジを持つ多変量`X`外れ値の影響を除去することです。観測値（`X`の行）は、2つの外れ値性指標に基づいて重みを受け取ります：

1. スタヘル-ドノホの外れ値性 (Maronna and Yohai, 1995) が`X`に対して計算されます（関数`outstah`）。外れ値性値が最も高い観測値の割合`prm`は重みw1 = 0を受け取り（他は重みw1 = 1を受け取る）。
2. 中心へのユークリッド距離に基づく外れ値性が計算されます（関数`outstah`）。外れ値性値が最も高い観測値の割合`prm`は重みw2 = 0を受け取り（他は重みw2 = 1を受け取る）。

観測値の最終的な重みは、重み.weights * w1 * w2によって計算され、重み付きPCAで使用されます。

デフォルトでは、関数は`prm = .3`を使用します（Hubert et al. 2005, 2009のROBPCAアルゴリズムのように）。

## 参考文献

Hubert, M., Rousseeuw, V.J., Vanden Branden, K., 2005. ROBPCA: A New Approach to Robust Principal  Component Analysis. Technometrics 47, 64-79. https://doi.org/10.1198/004017004000000563

Hubert, M., Rousseeuw, V., Verdonck, T., 2009. Robust PCA for skewed data and its outlier map. Computational  Statistics & Data Analysis 53, 2264-2274. https://doi.org/10.1016/j.csda.2008.05.027

Maronna, R.A., Yohai, V.J., 1995. The Behavior of the Stahel-Donoho Robust Multivariate Estimator.  Journal of the American Statistical Association 90, 330–341.  https://doi.org/10.1080/01621459.1995.10476517

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
model = pcaout(; nlv)  
#model = pcasvd(; nlv) 
fit!(model, X)
@names model
@names model.fitm
@head T = model.fitm.T
## 同じ：
transf(model, X)

i = 1
plotxy(T[:, i], T[:, i + 1]; zeros = true, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1)).f
```
