```
snv(; kwargs...)
snv(X; kwargs...)
```

各行のXデータの標準正規変数（SNV）変換。

  * `X` : Xデータ (n, p)。

キーワード引数：

  * `centr` : 中心化が行われるかどうかを示すブール値。
  * `scal` : スケーリングが行われるかどうかを示すブール値。

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

model = snv() 
#model = snv(scal = false) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
@head rowmean(Xptrain)
@head rowstd(Xptrain)
@head rowmean(Xptest)
@head rowstd(Xptest)
```
