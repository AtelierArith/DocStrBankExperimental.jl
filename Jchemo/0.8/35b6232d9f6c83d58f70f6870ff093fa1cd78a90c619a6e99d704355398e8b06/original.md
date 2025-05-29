```
aicplsr(X, y; alpha = 2, kwargs...)
```

Compute Akaike's (AIC) and Mallows's (Cp) criteria for univariate PLSR models.

  * `X` : X-data (n, p).
  * `y` : Univariate Y-data.

Keyword arguments:

  * Same arguments as those of function `cglsr`.
  * `alpha` : Coefficient multiplicating   the model complexity (df) to compute AIC.

The function uses function `dfplsr_cg`. 

## References

Hansen, P.C., 1998. Rank-Deficient and Discrete Ill-Posed Problems, Mathematical Modeling and Computation.  Society for Industrial and Applied Mathematics. https://doi.org/10.1137/1.9780898719697

Hansen, P.C., 2008. Regularization Tools version 4.0 for Matlab 7.3.  Numer Algor 46, 189–194. https://doi.org/10.1007/s11075-007-9136-9

Lesnoff, M., Roger, J.-M., Rutledge, D.N., 2021. Monte Carlo methods for estimating  Mallows’s Cp and AIC criteria for PLSR models. Illustration on agronomic spectroscopic NIR data.  Journal of Chemometrics n/a, e3369. https://doi.org/10.1002/cem.3369

## Examples

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
