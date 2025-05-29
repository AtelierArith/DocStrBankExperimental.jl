```
dmkern(; kwargs...)
dmkern(X; kwargs...)
```

ガウスカーネル密度推定 (KDE)。

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `h` : バンド幅を定義します。例を参照してください。
  * `a` : スコットのルールの定数 (デフォルトのバンド幅)、その後を参照してください。

非パラメトリックガウスカーネルによる `X` (列空間) の確率密度の推定。

データ `X` は単変量 (p = 1) または多変量 (p > 1) である可能性があります。後者の場合、関数 `dmkern` は Scott & Sain 2005 Eq.19 のような乗法カーネルを計算し、内部バンド幅行列 `H` は対角行列です (コードを参照してください)。

**注意:** `dmkern` コード内の `H` は、文献ではしばしば "H^(1/2)" と表記されます (例: Wikipedia)。

デフォルトのバンド幅は次のように計算されます:

  * `h` = `a` * n^(-1 / (p + 4)) * colstd(`X`)

(`a` = 1 は Scott & Sain 2005 におけるものです)。

## 参考文献

Scott, D.W., Sain, S.R., 2005. 9 - 多次元密度推定, in: Rao, C.R., Wegman, E.J., Solka, J.L. (Eds.), 統計学ハンドブック, データマイニングとデータビジュアライゼーション. エルゼビア, pp. 229–261. https://doi.org/10.1016/S0169-7161(04)24009-3

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

model = dmkern()
fit!(model, T) 
@names model.fitm
model.fitm.H
u = [1; 4; 150]
predict(model, T[u, :]).pred

h = .3
model = dmkern(; h)
fit!(model, T) 
model.fitm.H
predict(model, T[u, :]).pred

h = [.3; .1]
model = dmkern(; h)
fit!(model, T) 
model.fitm.H
predict(model, T[u, :]).pred

## 二変量分布
npoints = 2^7
nlv = 2
lims = [(minimum(T[:, j]), maximum(T[:, j])) for j = 1:nlv]
x1 = LinRange(lims[1][1], lims[1][2], npoints)
x2 = LinRange(lims[2][1], lims[2][2], npoints)
z = mpar(x1 = x1, x2 = x2)
grid = reduce(hcat, z)
m = nro(grid)
model = dmkern() 
#model = dmkern(a = .5) 
#model = dmkern(h = .3) 
fit!(model, T) 

res = predict(model, grid) ;
pred_grid = vec(res.pred)
f = Figure(size = (600, 400))
ax = Axis(f[1, 1];  title = "FDAスコアの密度 (アイリス)", xlabel = "スコア 1", 
    ylabel = "スコア 2")
co = contour!(ax, grid[:, 1], grid[:, 2], pred_grid; levels = 10, labels = true)
scatter!(ax, T[:, 1], T[:, 2], color = :red, markersize = 5)
#xlims!(ax, -15, 15) ;ylims!(ax, -15, 15)
f

## 単変量分布
x = T[:, 1]
model = dmkern() 
#model = dmkern(a = .5) 
#model = dmkern(h = .3) 
fit!(model, x) 
pred = predict(model, x).pred 
f = Figure()
ax = Axis(f[1, 1])
hist!(ax, x; bins = 30, normalization = :pdf)  # 面積 = 1
scatter!(ax, x, vec(pred); color = :red)
f

x = T[:, 1]
npoints = 2^8
lims = [minimum(x), maximum(x)]
#delta = 5 ; lims = [minimum(x) - delta, maximum(x) + delta]
grid = LinRange(lims[1], lims[2], npoints)
model = dmkern() 
#model = dmkern(a = .5) 
#model = dmkern(h = .3) 
fit!(model, x) 
pred_grid = predict(model, grid).pred 
f = Figure()
ax = Axis(f[1, 1])
hist!(ax, x; bins = 30, normalization = :pdf)  # 面積 = 1
lines!(ax, grid, vec(pred_grid); color = :red)
f
```
