```
scale()
scale(X)
scale(X, weights::Weight)
```

Xデータの列ごとのスケーリング。

  * `X` : Xデータ (n, p)。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/cassav.jld2") 
@load db dat
@names dat
X = dat.X
year = dat.Y.year
s = year .<= 2012
Xtrain = X[s, :]
Xtest = rmrow(X, s)
wlst = names(dat.X)
wl = parse.(Float64, wlst)
plotsp(X, wl; nsamp = 20).f

model = scale() 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
colstd(Xptrain)
@head Xptest 
@head Xtest ./ colstd(Xtrain)'
plotsp(Xptrain).f
plotsp(Xptest).f
```
