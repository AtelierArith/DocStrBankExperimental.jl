```
kplsr(; kwargs...)
kplsr(X, Y; kwargs...)
kplsr(X, Y, weights::Weight; kwargs...)
kplsr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

カーネル部分最小二乗回帰 (KPLSR) は、Nipalsアルゴリズムを用いて実装されています (Rosipal & Trejo, 2001)。

  * `X` : Xデータ (n, p)。
  * `Y` : Yデータ (n, q)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません (例えば、関数 `mweight` を参照)。

キーワード引数:

  * `nlv` : 考慮すべき潜在変数 (LV) の数。
  * `kern` : グラム行列を計算するために使用されるカーネルのタイプ。 可能な値は: `:krbf`, `:kpol`。 それぞれの関数 `krbf` と `kpol` のキーワード引数を参照してください。
  * `scal` : ブール値。 `true` の場合、`X` と `Y` の各列はその未修正の標準偏差でスケーリングされます。

このアルゴリズムは n > 1000 の場合に遅くなります。 代わりに関数 `dkplsr` を使用してください。

## 参考文献

Rosipal, R., Trejo, L.J., 2001. Kernel Partial Least Squares Regression in Reproducing Kernel Hilbert Space. Journal of Machine Learning Research 2, 97-123.

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

nlv = 20
kern = :krbf ; gamma = 1e-1
model = kplsr(; nlv, kern, gamma) ;
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
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

####### sinc(x) 関数のフィッティングの例
####### Rosipal & Trejo 2001 p. 105-106 に記載
x = collect(-10:.2:10) 
x[x .== 0] .= 1e-5
n = length(x)
zy = sin.(abs.(x)) ./ abs.(x) 
y = zy + .2 * randn(n) 
nlv = 2
kern = :krbf ; gamma = 1 / 3
model = kplsr(; nlv, kern, gamma) 
fit!(model, x, y)
pred = predict(model, x).pred 
f, ax = scatter(x, y) 
lines!(ax, x, zy, label = "真のモデル")
lines!(ax, x, vec(pred), label = "フィッティングモデル")
axislegend("方法")
f
```
