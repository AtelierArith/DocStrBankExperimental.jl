```
dfplsr_cg(X, y; kwargs...)
```

CGLSアルゴリズムを用いたPLSRモデルのモデルの複雑さ（df）を計算します。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量Yデータ。

キーワード引数:

  * 関数`cglsr`と同じ。

PLSRモデルの自由度（`df`）は、0, 1, ..., `nlv` LVsに対して返されます。

## 参考文献

Hansen, P.C., 1998. Rank-Deficient and Discrete Ill-Posed Problems,  Mathematical Modeling and Computation. Society for Industrial and  Applied Mathematics. https://doi.org/10.1137/1.9780898719697

Hansen, P.C., 2008. Regularization Tools version 4.0 for Matlab 7.3.  Numer Algor 46, 189–194. https://doi.org/10.1007/s11075-007-9136-9

Lesnoff, M., Roger, J.-M., Rutledge, D.N., 2021. Monte Carlo methods  for estimating Mallows’s Cp and AIC criteria for PLSR models. Illustration  on agronomic spectroscopic NIR data. Journal of Chemometrics n/a, e3369. https://doi.org/10.1002/cem.3369

## 例

```julia
## 以下の例は、Kramer & Sugiyama 2011によるオゾンデータに関する数値的な説明を再現します 
## （図1、中央）。
## df計算に使用される関数 "pls.model"
## Rパッケージ "plsdof" v0.2-9 (Kramer & Braun 2019)では
## PLSの前にX行列を自動的にスケーリングします。
## この例では、plsdofとの一貫性のためにXをスケーリングします。

using Jchemo, JchemoData, JLD2, DataFrames, CairoMakie 
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "ozone.jld2") 
@load db dat
@names dat
X = dat.X
dropmissing!(X) 
zX = rmcol(Matrix(X), 4) 
y = X[:, 4] 
## plsdofとの一貫性のために
xscales = colstd(zX)
zXs = fscale(zX, xscales)
## 終了

nlv = 12 ; gs = true
res = dfplsr_cg(zXs, y; nlv, gs) ;
res.df 
df_kramer = [1.000000, 3.712373, 6.456417, 11.633565, 
    12.156760, 11.715101, 12.349716,
    12.192682, 13.000000, 13.000000, 
    13.000000, 13.000000, 13.000000]
f, ax = plotgrid(0:nlv, df_kramer; step = 2, xlabel = "Nb. LVs", ylabel = "df")
scatter!(ax, 0:nlv, res.df; color = "red")
ablines!(ax, 1, 1; color = :grey, linestyle = :dot)
f
```
