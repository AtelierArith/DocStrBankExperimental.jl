```
pcapp(; kwargs...)
pcapp(X; kwargs...)
pcapp!(X::Matrix; kwargs...)
```

Robust PCA by projection pursuit.

  * `X` : X-data (n, p).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `nsim` : Nb. of additional (to X-rows) simulated directions for the projection pursuit.
  * `scal` : Boolean. If `true`, each column of `X` is scaled by its MAD.

For `nsim = 0`, this is the Croux & Ruiz-Gazen (C-R, 2005) PCA algorithm that uses a projection  pursuit (PP) method. Data `X` are robustly centered by the spatial median, and the observations are  projected to the "PP" directions defined by the observations (rows of `X`) after they are normed.  The first PCA loading vector is the direction (within the PP directions) that maximizes a given  'projection index', here the median absolute deviation (MAD). Then, `X` is deflated to this loading vector,  and the process is re-run to define the next loading vector. And so on. 

A possible extension of this algorithm is to randomly simulate additionnal candidate PP directions to the  n row observations. If `nsim > 0`, the function simulates `nsim` additional PP directions to the n initial  ones, as proposed in Hubert et al. (2005): random couples of observations are sampled in `X` and, for each  couple, the direction passes through the two observations of the couple (see function `simpphub`).

## References

Croux, C., Ruiz-Gazen, A., 2005. High breakdown estimators for principal components:  the projection-pursuit approach revisited. Journal of Multivariate Analysis 95, 206–226.  https://doi.org/10.1016/j.jmva.2004.08.002

Hubert, M., Rousseeuw, V.J., Vanden Branden, K., 2005. ROBPCA: A New Approach to Robust Principal  Component Analysis. Technometrics 47, 64-79. https://doi.org/10.1198/004017004000000563

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
model = pcapp(; nlv, nsim = 2000)  
#model = pcasvd(; nlv) 
fit!(model, X)
@names model
@names model.fitm
@head T = model.fitm.T
## Same as:
@head transf(model, X)

i = 1
plotxy(T[:, i], T[:, i + 1]; zeros = true, xlabel = string("PC", i), 
    ylabel = string("PC", i + 1)).f
```
