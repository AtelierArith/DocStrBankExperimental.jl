```
rosaplsr(; kwargs...)
rosaplsr(Xbl, Y; kwargs...)
rosaplsr(Xbl, Y, weights::Weight; kwargs...)
rosaplsr!(Xbl::Vector, Y::Matrix, weights::Weight; kwargs...)
```

マルチブロック ROSA PLSR (Liland et al. 2016)。

  * `Xbl` : Xデータのブロックのリスト（行列のベクトル）    通常、(n, p)データの関数 `mblock` の出力。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測の重み (n)。    `Weight` 型でなければならない（例えば、関数 `mweight` を参照）。

キーワード引数：

  * `nlv` : 計算する潜在変数 (LVs = スコア) の数。
  * `scal` : ブール値。`true` の場合、`Xbl` のブロックの各列    と `Y` はその未修正の標準偏差でスケーリングされる    （ブロックスケーリングの前に）。

この関数は、Liland et al. (2016) の元のアルゴリズムと以下の違いがあります：

  * スコア T（潜在変数 LVs）は 1 に正規化されていない。
  * 多変量 `Y` が許可されている。この場合、二乗残差が    列ごとに合計され、各グローバル LV の勝者ブロックを見つける    （したがって、Y列は同じスケールである必要がある）。

## 参考文献

Liland, K.H., Næs, T., Indahl, U.G., 2016. ROSA — a fast  extension of partial least squares regression for multiblock  data analysis. Journal of Chemometrics 30, 651–662.  https://doi.org/10.1002/cem.2824

## 例

```julia
using Jchemo, JchemoData, JLD2
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ham.jld2") 
@load db dat
@names dat 
X = dat.X
Y = dat.Y
y = Y.c1
group = dat.group
listbl = [1:11, 12:19, 20:25]
s = 1:6
Xbltrain = mblock(X[s, :], listbl)
Xbltest = mblock(rmrow(X, s), listbl)
ytrain = y[s]
ytest = rmrow(y, s) 
ntrain = nro(ytrain) 
ntest = nro(ytest) 
ntot = ntrain + ntest 
(ntot = ntot, ntrain , ntest)

nlv = 3
scal = false
#scal = true
model = rosaplsr(; nlv, scal)
fit!(model, Xbltrain, ytrain)
@names model 
@names model.fitm
@head model.fitm.T
@head transf(model, Xbltrain)
transf(model, Xbltest)

res = predict(model, Xbltest)
res.pred 
rmsep(res.pred, ytest)
```
