```
lwplsravg(; kwargs...)
lwplsravg(X, Y; kwargs...)
```

Averaging kNN-LWPLSR models with different numbers of latent variables (kNN-LWPLSR-AVG).

  * `X` : X-data (n, p).
  * `Y` : Y-data (n, q).

Keyword arguments:

  * `nlvdis` : Number of latent variables (LVs) to consider in the global PLS used for the dimension    reduction before computing the dissimilarities. If `nlvdis = 0`, there is no dimension reduction.   If `nlvdis = 0`, there is no dimension reduction.
  * `metric` : Type of dissimilarity used to select the neighbors and to compute the weights    (see function `getknn`). Possible values are: `:eucl` (Euclidean), `:mah` (Mahalanobis),    `:sam` (spectral angular distance), `:cor` (correlation distance).
  * `h` : A scalar defining the shape of the weight function computed by function `winvs`. Lower is h,    sharper is the function. See function `winvs` for details (keyword arguments `criw` and `squared` of    `winvs` can also be specified here).
  * `k` : The number of nearest neighbors to select for each observation to predict.
  * `tolw` : For stabilization when very close neighbors.
  * `nlv` : A range of nb. of latent variables (LVs)    to compute for the local (i.e. inside each neighborhood)    models.
  * `scal` : Boolean. If `true`, (a) each column of the global `X`    (and of the global `Y` if there is a preliminary PLS reduction dimension)    is scaled by its uncorrected standard deviation before to compute    the distances and the weights, and (b) the X and Y scaling is also done    within each neighborhood (local level) for the weighted PLSR.
  * `verbose` : Boolean. If `true`, predicting information are printed.

Ensemblist method where the predictions are computed by averaging the predictions of a set of  models built with different numbers of LVs, such as in Lesnoff 2023. On each neighborhood, a  PLSR-averaging (Lesnoff et al. 2022) is done instead of a PLSR.

For instance, if argument `nlv` is set to `nlv` = `5:10`, the prediction for a new observation is the  simple average of the predictions returned by the models with 5 LVs, 6 LVs, ... 10 LVs, respectively.

## References

Lesnoff, M., Andueza, D., Barotin, C., Barre, V., Bonnal, L., Fernández Pierna, J.A., Picard, F.,  Vermeulen, V., Roger, J.-M., 2022. Averaging and Stacking Partial Least Squares  Regression Models to Predict the Chemical Compositions and the Nutritive Values of Forages from  Spectral Near Infrared Data. Applied Sciences 12, 7850. https://doi.org/10.3390/app12157850

M. Lesnoff, Averaging a local PLSR pipeline to predict chemical compositions and nutritive values of forages  and feed from spectral near infrared data, Chemometrics and Intelligent Laboratory Systems. 244 (2023) 105031.  https://doi.org/10.1016/j.chemolab.2023.105031.

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

nlvdis = 5 ; metric = :mah 
h = 1 ; k = 200 ; nlv = 4:20
model = lwplsravg(; nlvdis, metric, h, k, nlv) ;
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm

res = predict(model, Xtest) ; 
@names res 
res.listnn
res.listd
res.listw
@head res.pred
@show rmsep(res.pred, ytest)
plotxy(res.pred, ytest; color = (:red, .5), bisect = true, xlabel = "Prediction",  
    ylabel = "Observed").f  
```
