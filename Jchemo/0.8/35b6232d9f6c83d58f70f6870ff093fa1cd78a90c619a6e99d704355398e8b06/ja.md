```
aicplsr(X, y; alpha = 2, kwargs...)
```

Akaikeの（AIC）およびMallowsの（Cp）基準を単変量PLSRモデルのために計算します。

  * `X` : Xデータ (n, p)。
  * `y` : 単変量Yデータ。

キーワード引数：

  * 関数`cglsr`の引数と同じ。
  * `alpha` : AICを計算するためにモデルの複雑さ（df）に掛ける係数。

この関数は関数`dfplsr_cg`を使用します。

## 参考文献

Hansen, P.C., 1998. Rank-Deficient and Discrete Ill-Posed Problems, Mathematical Modeling and Computation.  Society for Industrial and Applied Mathematics. https://doi.org/10.1137/1.9780898719697

Hansen, P.C., 2008. Regularization Tools version 4.0 for Matlab 7.3.  Numer Algor 46, 189–194. https://doi.org/10.1007/s11075-007-9136-9

Lesnoff, M., Roger, J.-M., Rutledge, D.N., 2021. Monte Carlo methods for estimating  Mallows’s Cp and AIC criteria for PLSR models. Illustration on agronomic spectroscopic NIR data.  Journal of Chemometrics n/a, e3369. https://doi.org/10.1002/cem.3369

## 例

```julia
using Jchemo, JchemoData, CairoMakie
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "cassav.jld2") 
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

nlv = 40
res = aicplsr(X, y; nlv) ;
res.crit
res.opt
res.delta

zaic = res.crit.aic
f, ax = plotgrid(0:nlv, zaic; xlabel = "Nb. LVs", ylabel = "AIC")
scatter!(ax, 0:nlv, zaic)
f
```
