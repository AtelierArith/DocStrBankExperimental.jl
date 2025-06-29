```
pcaout(; kwargs...)
pcaout(X; kwargs...)
pcaout(X, weights::Weight; kwargs...)
pcaout!(X::Matrix, weights::Weight; kwargs...)
```

Robust PCA using outlierness.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `prm` : Proportion of the data removed (hard rejection of outliers) for each outlierness measure.
  * `scal` : Boolean. If `true`, each column of `X` is scaled by its MAD when computing the outlierness    and by its uncorrected standard deviation when computing weighted PCA.

Robust PCA combining outlyingness measures and weighted PCA (WPCA). 

The objective is to remove the effect of multivariate `X`-outliers that have potentially bad leverages.  Observations (`X`-rows) receive weights depending on two outlyingness indicators:

1. The Stahel-Donoho outlyingness (Maronna and Yohai, 1995) is computed (function `outstah`) on `X`.   The proportion `prm` of the observations with the highest outlyingness values receive a weight w1 = 0   (the other receive a weight w1 = 1).
2. An outlyingness based on the Euclidean distance to center (function `outstah`) is computed. The proportion `prm`   of the observations with the highest outlyingness values receive a weight w2 = 0 (the other receive a weight w2 = 1).

The final weights of the observations are computed by weights.w * w1 * w2 that is used in a weighted PCA.

By default, the function uses `prm = .3` (such as in the ROBPCA algorithm of Hubert et al. 2005, 2009). 

## References

Hubert, M., Rousseeuw, V.J., Vanden Branden, K., 2005. ROBPCA: A New Approach to Robust Principal  Component Analysis. Technometrics 47, 64-79. https://doi.org/10.1198/004017004000000563

Hubert, M., Rousseeuw, V., Verdonck, T., 2009. Robust PCA for skewed data and its outlier map. Computational  Statistics & Data Analysis 53, 2264-2274. https://doi.org/10.1016/j.csda.2008.05.027

Maronna, R.A., Yohai, V.J., 1995. The Behavior of the Stahel-Donoho Robust Multivariate Estimator.  Journal of the American Statistical Association 90, 330–341.  https://doi.org/10.1080/01621459.1995.10476517

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
mypath = dirname(dirname(pathof(JchemoData)))
db = joinpath(mypath, "data", "octane.jld2") 
@load db dat
@names dat
X = dat.X 
wlst = names(X)
wl = parse.(Float64, wlst)
n = nro(X)

nlv = 3
model = pcaout(; nlv)  
#model = pcasvd(; nlv) 
fit!(model, X)
@names model
@names model.fitm
@head T = model.fitm.T
## Same as:
transf(model, X)

i = 1
plotxy(T[:, i], T[:, i + 1]; zeros = true, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1)).f
```
