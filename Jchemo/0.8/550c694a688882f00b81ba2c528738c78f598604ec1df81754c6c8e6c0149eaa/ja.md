```
dmnormlog(; kwargs...)
dmnormlog(X; kwargs...)
dmnormlog!(X::Matrix; kwargs...)
dmnormlog(mu, S; kwargs...)
dmnormlog!(mu::Vector, S::Matrix; kwargs...)
```

正規確率密度推定の対数。     * `X` : 平均 `mu` と共分散行列 `S` を推定するために使用される Xデータ (n, p)。 `X` が指定されていない場合、`mu` と `S` は `kwargs` で提供されなければなりません。     * `mu` : 正規分布の平均ベクトル。      * `S` : 正規分布の共分散行列。 キーワード引数:     * `simpl` : ブール値。 `true` の場合、正規密度式の定数項と行列式は 1 に設定されます。

関数 `dmnorm` のヘルプページを参照してください。

## 例

```julia
using Jchemo, JchemoData, JLD2, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "iris.jld2") 
@load db dat
@names dat
X = dat.X[:, 1:4] 
y = dat.X[:, 5]
n = nro(X)
tab(y) 

## セトサクラスの例 
s = y .== "setosa"
zX = X[s, :]

model = dmnormlog()
fit!(model, zX)
fitm = model.fitm
@names fitm
fitm.Uinv 
fitm.logdetS
@head pred = predict(model, zX).pred

## dmnormとの一貫性
model0 = dmnorm()
fit!(model0, zX)
@head pred0 = predict(model0, zX).pred
@head log.(pred0)
```
