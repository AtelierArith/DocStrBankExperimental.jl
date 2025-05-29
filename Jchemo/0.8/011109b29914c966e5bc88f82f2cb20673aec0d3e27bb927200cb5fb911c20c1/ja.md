```
umap(; kwargs...)
umap(X; kwargs...)
```

UMAP: 一様多様体近似と次元削減のための射影

  * `X` : Xデータ (n, p)。

キーワード引数:

  * `nlv` : 計算する潜在変数 (LV) の数。
  * `psamp` : トレーニング用の `X` におけるサンプリングの割合。
  * `n_neighbors` : 初期の高次元グラフを構築するために使用される近似近傍の数。
  * `min_dist` : 低次元空間における点間の最小距離。
  * `scal` : ブール値。`true` の場合、`X` と `Y` の各列はその未修正の標準偏差でスケーリングされる。

この関数は、パッケージ `UMAP.jl` を使用してUMAP次元削減を適合させます。使用されるメトリックはユークリッド距離です。

`psamp < 1` の場合、観測値 (行の `X`) の割合 `psamp` のみがモデルを構築するために使用されます (XのPCAの最初のスコアに対する系統的サンプリング)。nが大きい場合の計算時間を短縮するために使用できます。

## 参考文献

https://github.com/dillondaudert/UMAP.jl

McInnes, L, Healy, J, Melville, J, UMAP: 一様多様体近似と次元削減のための射影。ArXiV 1802.03426, 2018 https://arxiv.org/abs/1802.03426

https://umap-learn.readthedocs.io/en/latest/how*umap*works.html

https://pair-code.github.io/understanding-umap/ 

## 例

```julia
using Jchemo, JchemoData
using JLD2, GLMakie, CairoMakie, FreqTables
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "challenge2018.jld2") 
@load db dat
@names dat
X = dat.X 
Y = dat.Y
wlst = names(X)
wl = parse.(Float64, wlst)
ntot = nro(X)
summ(Y)
typ = Y.typ
test = Y.test
y = Y.conc

model1 = snv() 
model2 = savgol(npoint = 21, deriv = 2, degree = 3)
model = pip(model1, model2)
fit!(model, X)
@head Xp = transf(model, X)
plotsp(Xp, wl; xlabel = "波長 (nm)", ylabel = "吸光度", nsamp = 20).f

s = Bool.(test)
Xtrain = rmrow(Xp, s)
Ytrain = rmrow(Y, s)
ytrain = rmrow(y, s)
typtrain = rmrow(typ, s)
Xtest = Xp[s, :]
Ytest = Y[s, :]
ytest = y[s]
typtest = typ[s]
ntrain = nro(Xtrain)
ntest = nro(Xtest)
(ntot = ntot, ntrain, ntest)

freqtable(string.(typ, "-", Y.label))
freqtable(typ, test)

#################

nlv = 3
n_neighbors = 50 ; min_dist = .5 
model = umap(; nlv, n_neighbors, min_dist)  
fit!(model, Xtrain)
@head T = model.fitm.T
@head Ttest = transf(model, Xtest)

nlv = 3
n_neighbors = 50 ; min_dist = .5 
model = umap(; nlv, n_neighbors, min_dist)  
fit!(model, Xtrain)
@head T = model.fitm.T
@head Ttest = transf(model, Xtest)
GLMakie.activate!() 
#CairoMakie.activate!()
lev = mlev(typtrain)
nlev = length(lev)
colsh = :tab10
colm = cgrad(colsh, nlev; alpha = .7, categorical = true) 
ztyp = recod_catbyint(typtrain)
f = Figure()
i = 1
ax = Axis3(f[1, 1], xlabel = string("LV", i), ylabel = string("LV", i + 1), 
        zlabel = string("LV", i + 2), title = "UMAP", perspectiveness = 0) 
scatter!(ax, T[:, i], T[:, i + 1], T[:, i + 2]; markersize = 8, 
    color = ztyp, colormap = colm) 
scatter!(ax, Ttest[:, i], Ttest[:, i + 1], Ttest[:, i + 2], color = :black, 
    markersize = 10)  
elt = [MarkerElement(color = colm[i], marker = '●', markersize = 10) for i in eachindex(lev)]
#elt = [PolyElement(polycolor = colm[i]) for i in eachindex(lev)]
title = "グループ"
Legend(f[1, 2], elt, lev, title; nbanks = 1, rowgap = 10, framevisible = false)
f
```
