```
pcasvd(; kwargs...)
pcasvd(X; kwargs...)
pcasvd(X, weights::Weight; kwargs...)
pcasvd!(X::Matrix, weights::Weight; kwargs...)
```

PCA by SVD factorization.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of principal components (PCs).
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

Let us note D the (n, n) diagonal matrix of weights (`weights.w`) and X the centered matrix in metric D. The function minimizes ||X - T * V'||^2  in metric D, by  computing a SVD factorization of sqrt(D) * X:

  * sqrt(D) * X ~ U * S * V'

Outputs are:

  * `T` = D^(-1/2) * U * S
  * `V` = V
  * The diagonal of S

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
@head Xtrain = X[s.train, :]
@head Xtest = X[s.test, :]

nlv = 3
model = pcasvd(; nlv)
#model = pcaeigen(; nlv)
#model = pcaeigenk(; nlv)
#model = pcanipals(; nlv)
fit!(model, Xtrain)
@names model
@names model.fitm
@head T = model.fitm.T
## Same as:
@head transf(model, X)
T' * T
@head V = model.fitm.V
V' * V

@head Ttest = transf(model, Xtest)

res = summary(model, Xtrain) ;
@names res
res.explvarx
res.contr_var
res.coord_var
res.cor_circle
```
