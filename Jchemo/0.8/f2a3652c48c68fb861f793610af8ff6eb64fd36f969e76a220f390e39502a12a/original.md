```
rrr(; kwargs...)
rrr(X, Y; kwargs...)
rrr(X, Y, weights::Weight; kwargs...)
rr!(X::Matrix, Y::Matrix, weights::Weight; kwargs...)
```

Reduced rank regression (RRR, a.k.a RA).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `tau` : Regularization parameter (∊ [0, 1]).
  * `tol` : Tolerance for the Nipals algorithm.
  * `maxit` : Maximum number of iterations for the Nipals algorithm.
  * `scal` : Boolean. If `true`, each column of `X` and `Y`    is scaled by its uncorrected standard deviation.

Reduced rank regression, also referred to as redundancy analysis (RA) regression.  In this function, the RA uses the Nipals algorithm presented in Mangamana et al 2021,  section 2.1.1.

A continuum regularization is available. After block centering and scaling, the covariances  matrices are computed as follows: 

  * Cx = (1 - `tau`) * X'DX + `tau` * Ix

where D is the observation (row) metric. Value `tau` = 0 can generate unstability when  inverting the covariance matrices. A better alternative is generally to use an epsilon value  (e.g. `tau` = 1e-8) to get similar results as with pseudo-inverses.  

## References

Bougeard, S., Qannari, E.M., Lupo, C., Chauvin, C., 2011. Multiblock redundancy analysis from  a user’s perspective. Application in veterinary epidemiology. Electronic Journal of  Applied Statistical Analysis 4, 203-214–214. https://doi.org/10.1285/i20705948v4n2p203

Bougeard, S., Qannari, E.M., Rose, N., 2011. Multiblock redundancy analysis: interpretation tools  and application in epidemiology. Journal of Chemometrics 25, 467–475. https://doi.org/10.1002/cem.1392 

Tchandao Mangamana, E., Glèlè Kakaï, R., Qannari, E.M., 2021. A general strategy for setting up supervised  methods of multiblock data analysis. Chemometrics and Intelligent Laboratory Systems 217, 104388.  https://doi.org/10.1016/j.chemolab.2021.104388

## Examples

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

nlv = 1
tau = 1e-4
model = rrr(; nlv, tau) 
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
```
