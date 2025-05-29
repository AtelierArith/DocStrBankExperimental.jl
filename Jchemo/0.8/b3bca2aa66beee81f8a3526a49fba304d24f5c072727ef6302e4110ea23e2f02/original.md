```
fda(; kwargs...)
fda(X, y; kwargs...)
fda(X, y, weights; kwargs...)
fda!(X::Matrix, y, weights; kwargs...)
```

Factorial discriminant analysis (FDA).

  * `X` : X-data (n, p).
  * `y` : y-data (n) (class membership).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. of discriminant components.
  * `lb` : Ridge regularization parameter "lambda".   Can be used when `X` has collinearities.
  * `prior` : Type of prior probabilities for class    membership. Possible values are: `:unif` (uniform),    `:prop` (proportional), or a vector (of length equal to    the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

FDA by eigen factorization of Inverse(W) * B, where W is  the "Within"-covariance matrix (pooled over the classes),  and B the "Between"-covariance matrix.

The function maximizes the consensus:

  * p'Bp / p'Wp

i.e. max p'Bp with constraint p'Wp = 1. Vectors p (columns of `V`)  are the linear discrimant coefficients often referred to as "LD".

If `X` is ill-conditionned, a ridge regularization can be used:

  * If `lb` > 0, W is replaced by W + `lb` * I,    where I is the Idendity matrix.

In the high-level version of the present functions, the observation  weights are automatically defined by the given priors (argument `prior`):  the sub-totals by class of the observation weights are set equal to the prior  probabilities. The low-level version (argument `weights`) allows to implement  other choices.

## Examples

```julia
using Jchemo, JchemoData, JLD2, CairoMakie 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
y = dat.X[:, 5]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
ytrain = y[s.train]
Xtest = X[s.test, :]
ytest = y[s.test]
tab(ytrain)
tab(ytest)

nlv = 2
model = fda(; nlv)
#model = fdasvd(; nlv)
fit!(model, Xtrain, ytrain)
@names model
@names model.fitm
fitm = model.fitm ;
lev = fitm.lev
nlev = length(lev)
fitm.priors
aggsumv(fitm.weights.w, ytrain)

@head fitm.T 
@head transf(model, Xtrain)
@head transf(model, Xtest)

## X-loadings matrix
## = coefficients of the linear discriminant function
## = "LD" of function lda of the R package MASS
fitm.V
fitm.V' * fitm.V

## Explained variance computed by weighted PCA 
## of the class centers in transformed scale
summary(model).explvarx

## Projections of the class centers 
## to the score space
ct = fitm.Tcenters 
f, ax = plotxy(fitm.T[:, 1], fitm.T[:, 2], ytrain; ellipse = true, title = "FDA",
    xlabel = "Score-1", ylabel = "Score-2")
scatter!(ax, ct[:, 1], ct[:, 2], marker = :star5, markersize = 15, color = :red)  # see available_marker_symbols()
f
```
