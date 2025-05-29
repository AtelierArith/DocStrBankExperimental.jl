```
splsr(; kwargs...)
splsr(X, Y; kwargs...)
splsr(X, Y, weights::Weight; kwargs...)
splsr!(X::Matrix, Y::Union{Matrix, BitMatrix}, weights::Weight; kwargs...)
```

Sparse partial least squares regression (Lê Cao et al. 2008)

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. latent variables (LVs) to compute.
  * `meth` : Method used for the sparse thresholding.    Possible values are: `:soft`, `:hard`. See thereafter.
  * `nvar` : Nb. variables (`X`-columns) selected for each LV.    Can be a single integer (i.e. same nb. of variables for each LV),    or a vector of length `nlv`.
  * `scal` : Boolean. If `true`, each column of `X` and `Y` is    scaled by its uncorrected standard deviation.

Adaptation of the sparse partial least squares regression algorihm of  Lê Cao et al. 2008. The fast "improved kernel algorithm #1" of  Dayal & McGregor (1997) is used instead Nipals. 

In the present version of `splsr`, the sparse thresholding only concerns  `X`. The function provides two thresholding methods to compute the sparse  `X`-loading weights w (`:soft` and `:hard`), see function `spca` for description. 

The case `meth = :soft` returns the same results as function `spls` of  the R package mixOmics (Lê Cao et al.) with the regression mode and without  sparseness on `Y`.

The COVSEL regression method described in Roger et al 2011 (see also Höskuldsson 1992) is implemented by setting `nvar = 1`.

## References

Dayal, B.S., MacGregor, J.F., 1997. Improved PLS algorithms.  Journal of Chemometrics 11, 73-85.

Höskuldsson, A., 1992. The H-principle in modelling with applications  to chemometrics. Chemometrics and Intelligent Laboratory Systems,  Proceedings of the 2nd Scandinavian Symposium on Chemometrics 14,  139–153. https://doi.org/10.1016/0169-7439(92)80099-P

Lê Cao, K.-A., Rossouw, D., Robert-Granié, C., Besse, P., 2008.  A Sparse PLS for Variable Selection when Integrating Omics Data.  Statistical Applications in Genetics and Molecular Biology 7.  https://doi.org/10.2202/1544-6115.1390

Kim-Anh Lê Cao, Florian Rohart, Ignacio Gonzalez, Sebastien Dejean  with key contributors Benoit Gautier, Francois Bartolo, contributions  from Pierre Monget, Jeff Coquery, FangZou Yao and Benoit Liquet.  (2016). mixOmics: Omics Data Integration Project. R package  version 6.1.1. https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Package mixOmics on Bioconductor: https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Roger, J.M., Palagos, B., Bertrand, D., Fernandez-Ahumada, E., 2011.  covsel: Variable selection for highly multivariate and multi-response  calibration: Application to IR spectroscopy.  Chem. Lab. Int. Syst. 106, 216-223.

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

nlv = 15
meth = :soft
#meth = :hard
nvar = 20
model = splsr(; nlv, meth, nvar) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
@head model.fitm.T
@head model.fitm.W

coef(model)
coef(model; nlv = 3)

@head transf(model, Xtest)
@head transf(model, Xtest; nlv = 3)

res = predict(model, Xtest)
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction", 
    ylabel = "Observed").f    

res = summary(model, Xtrain) ;
@names res
z = res.explvarx
plotgrid(z.nlv, z.cumpvar; step = 2, xlabel = "Nb. LVs", 
    ylabel = "Prop. Explained X-Variance").f
```
