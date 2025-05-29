```
fdif(; kwargs...)
fdif(X; kwargs...)
```

各行のXデータに対する有限差分（離散導関数）。

  * `X` : Xデータ (n, p)。

キーワード引数：

  * `npoint` : 有限差分のウィンドウに関与するポイント数。ウィンドウの範囲（＝2つの連続する列の間隔の数）はnpoint - 1です。

このメソッドは列の次元を減少させます：

  * (n, p) –> (n, p - npoint + 1)。

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

model = fdif(npoint = 2) 
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
