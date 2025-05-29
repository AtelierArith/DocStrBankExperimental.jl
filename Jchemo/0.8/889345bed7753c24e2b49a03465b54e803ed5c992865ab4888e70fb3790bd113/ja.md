```
spcr(; kwargs...)
spcr(X, Y; kwargs...)
spcr(X, Y, weights::Weight; kwargs...)
spcr!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

スパース主成分回帰 (sPCR)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * 関数 `spca` と同じ。

スパースPCAから計算されたスコアに基づく回帰 (Shen & Huang 2008 の sPCA-rSVDアルゴリズム)。 詳細は関数 `spca` を参照。

## 参考文献

Shen, H., Huang, J.Z., 2008. スパース主成分分析による正則化低ランク行列近似。 多変量解析ジャーナル 99, 1015–1034. https://doi.org/10.1016/j.jmva.2007.06.007

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X 
y = dat.Y.tbc
year = dat.Y.year
tab(year)
s = year .<= 2012
Xtrain = X[s, :]
ytrain = y[s]
Xtest = rmrow(X, s)
ytest = rmrow(y, s)

nlv = 15
meth = :soft
#meth = :hard
nvar = 20 
model = spcr(; nlv, meth, nvar, defl = :t) ;
fit!(model, Xtrain, ytrain)
@names model
fitm = model.fitm ;
@names fitm
@head fitm.fitm.T
@head transf(model, X)
@head fitm.fitm.V

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "Nb. LVs", 
    ylabel = "Prop. Explained X-Variance").f
```
