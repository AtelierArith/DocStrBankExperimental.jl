```
detrend_pol(; kwargs...)
detrend_pol(X; kwargs...)
```

Xデータの各行のベースライン補正を多項式線形回帰によって行います。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `degree` : 多項式の次数。

デトレンド変換: この関数は各観測値に対して多項式回帰によってベースラインをフィットさせ、残差（＝ベースラインから補正された信号）を返します。

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

model = detrend_pol(degree = 2)
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain, wl).f
plotsp(Xptest, wl).f

## 1つのスペクトルの例
i = 2
zX = Matrix(X)[i:i, :]
model = detrend_pol(degree = 1)
fit!(model, zX)
zXc = transf(model, zX)   # = 補正されたスペクトル 
B = zX - zXc            # = 推定されたベースライン
f, ax = plotsp(zX, wl)
lines!(wl, vec(B); color = :blue)
lines!(wl, vec(zXc); color = :black)
f
```
