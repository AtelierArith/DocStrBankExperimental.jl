```
pcr(; kwargs...)
pcr(X, Y; kwargs...)
pcr(X, Y, weights::Weight; kwargs...)
pcr!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

主成分回帰 (PCR) を SVD 分解を用いて行います。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。`Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * 関数 `pcasvd` と同じ

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
model = pcr(; nlv) ;
fit!(model, Xtrain, ytrain)
@names model
fitm = model.fitm ;
@names fitm
@names fitm.fitm

@head fitm.fitm.T
@head transf(model, X)

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

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "LVの数", ylabel = "説明されたX分散の割合").f
```
