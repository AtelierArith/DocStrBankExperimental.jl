```
interpl(; kwargs...)
interpl(X; kwargs...)
```

補間によるスペクトルのサンプリング。

  * `X` : スペクトルの行列 (n, p)。

キーワード引数:

  * `wl` : `X` の列 "名前" を表す値。長さ p の数値ベクトル、または増加する値を持つ AbstractRange でなければなりません。
  * `wlfin` : 各スペクトルを補間する `wl` の範囲内の最終値。数値ベクトル、または増加する値を持つ AbstractRange でなければなりません。

この関数は、パッケージ DataInterpolations.jl を使用して三次スプライン補間を実装しています。

## 参考文献

パッケージ DAtaInterpolations.jl https://github.com/PumasAI/DataInterpolations.jl https://htmlpreview.github.io/?https://github.com/PumasAI/DataInterpolations.jl/blob/v2.0.0/example/DataInterpolations.html

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

wlfin = range(500, 2400, length = 10)
#wlfin = collect(range(500, 2400, length = 10))
model = interpl(; wl, wlfin)
fit!(model, Xtrain)
Xptrain = transf(model, Xtrain)
Xptest = transf(model, Xtest)
plotsp(Xptrain).f
plotsp(Xptest).f
```
