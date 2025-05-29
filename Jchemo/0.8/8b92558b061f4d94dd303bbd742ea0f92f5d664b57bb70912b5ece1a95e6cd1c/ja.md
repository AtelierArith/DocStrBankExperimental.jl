```
plsrout(; kwargs...)
plsrout(X, Y; kwargs...)
plsrout(X, Y, weights::Weight; kwargs...)
pcaout!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

外れ値性を用いたロバストPLSR。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 潜在変数 (LV) の数。
  * `prm` : 各外れ値性測定のために除去されるデータの割合（外れ値の厳しい拒否）。
  * `scal` : ブール値。`true`の場合、外れ値性を計算する際に`X`の各列はそのMADでスケーリングされ、重み付きPCAを計算する際にはその未修正標準偏差でスケーリングされます。

外れ値性測定と重み付きPLSR (WPLSR) を組み合わせたロバストPLSR。これは関数`pcaout`と同じ原理ですが、最終ステップは重み付きPCAの代わりに重み付きPLSRです。  

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
model = plsrout(; nlv)
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "予測",  
    ylabel = "観測値").f    

res = predict(model, Xtest; nlv = 1:2)
@head res.pred[1]
@head res.pred[2]
```
