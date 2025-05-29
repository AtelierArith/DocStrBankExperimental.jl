```
dmnorm(; kwargs...)
dmnorm(X; kwargs...)
dmnorm!(X::Matrix; kwargs...)
dmnorm(mu, S; kwargs...)
dmnorm!(mu::Vector, S::Matrix; kwargs...)
```

正規確率密度推定。

  * `X` : 平均 `mu` と共分散行列 `S` を推定するために使用される Xデータ (n, p)。`X` が指定されていない場合、`mu` と `S` は `kwargs` で提供されなければなりません。
  * `mu` : 正規分布の平均ベクトル。
  * `S` : 正規分布の共分散行列。

キーワード引数：

  * `simpl` : ブール値。`true` の場合、正規密度式の定数項と行列式が 1 に設定されます。

データ `X` は単変量 (p = 1) または多変量 (p > 1) である可能性があります。例を参照してください。

`simple` = `true` の場合、共分散行列の行列式 (オブジェクト `detS`) と定数 (2 * pi)^(-p / 2) (オブジェクト `cst`) は 1 に設定されます。この関数は、中心 `mu` への二乗マハラノビス距離 d に収束する擬似密度を返します。これは、例えば、`X` の列数 (p) が大きくなりすぎる場合に役立つ可能性があります。その結果として：

  * `detS` が 0 に近づくか、逆に無限大に近づく；
  * `cst` が 0 に近づく、

これにより、真の密度を計算することが不可能になります。

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

nlv = 2
model0 = fda(; nlv)
fit!(model0, X, y)
@head T = transf(model0, X)
n, p = size(T)

#### FDAスコア空間における確率密度 (2D)
#### セトサクラスの例 
s = y .== "setosa"
zT = T[s, :]
m = nro(zT)

#### 二変量分布
model = dmnorm()
fit!(model, zT)
fitm = model.fitm
@names fitm
fitm.Uinv 
fitm.detS
@head pred = predict(model, zT).pred

## 直接構文
mu = colmean(zT)
S = covm(zT, mweight(ones(m))) * m / (m - 1) # 補正された共分散行列
fitm = dmnorm(mu, S) ; 
@names fitm
fitm.Uinv
fitm.detS

npoints = 2^7
lims = [(minimum(zT[:, j]), maximum(zT[:, j])) for j = 1:nlv]
x1 = LinRange(lims[1][1], lims[1][2], npoints)
x2 = LinRange(lims[2][1], lims[2][2], npoints)
z = mpar(x1 = x1, x2 = x2)
grid = reduce(hcat, z)
model = dmnorm()
fit!(model, zT)
res = predict(model, grid) ;
pred_grid = vec(res.pred)
f = Figure(size = (600, 400))
ax = Axis(f[1, 1];  title = "FDAスコアの密度 (アイリス - セトサ)", 
    xlabel = "スコア 1", ylabel = "スコア 2")
co = contour!(ax, grid[:, 1], grid[:, 2], pred_grid; levels = 10, labels = true)
scatter!(ax, T[:, 1], T[:, 2], color = :red, markersize = 5)
scatter!(ax, zT[:, 1], zT[:, 2], color = :blue, markersize = 5)
#xlims!(ax, -12, 12) ;ylims!(ax, -12, 12)
f

#### 単変量分布
j = 1
x = zT[:, j]
model = dmnorm()
fit!(model, x)
pred = predict(model, x).pred 
f = Figure()
ax = Axis(f[1, 1]; xlabel = string("FDAスコア ", j))
hist!(ax, x; bins = 30, normalization = :pdf)  # 面積 = 1
scatter!(ax, x, vec(pred); color = :red)
f

x = zT[:, j]
npoints = 2^8
lims = [minimum(x), maximum(x)]
#delta = 5 ; lims = [minimum(x) - delta, maximum(x) + delta]
grid = LinRange(lims[1], lims[2], npoints)
model = dmnorm()
fit!(model, x)
pred_grid = predict(model, grid).pred 
f = Figure()
ax = Axis(f[1, 1]; xlabel = string("FDAスコア ", j))
hist!(ax, x; bins = 30, normalization = :pdf)  # 面積 = 1
lines!(ax, grid, vec(pred_grid); color = :red)
f
```
