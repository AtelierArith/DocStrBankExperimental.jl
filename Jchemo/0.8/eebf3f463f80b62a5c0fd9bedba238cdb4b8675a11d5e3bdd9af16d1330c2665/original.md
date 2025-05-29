```
rda(; kwargs...)
rda(X, y; kwargs...)
rda(X, y, weights::Weight; kwargs...)
```

Regularized discriminant analysis (RDA).

  * `X` : X-data (n, p).
  * `y` : Univariate class membership (n).
  * `weights` : Weights (n) of the observations. Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `prior` : Type of prior probabilities for class membership. Possible values are: `:prop` (proportionnal),    `:unif` (uniform), or a vector (of length equal to the number of classes) giving the prior weight for each class    (in case of vector, it must be sorted in the same order as `mlev(y)`).
  * `alpha` : Scalar (∈ [0, 1]) defining the continuum between QDA (`alpha = 0`) and LDA (`alpha = 1`).
  * `lb` : Ridge regularization parameter "lambda" (>= 0).
  * `simpl` : Boolean. See function `dmnorm`.
  * `scal` : Boolean. If `true`, each column of `X` is scaled by its uncorrected standard deviation.

Let us note W the (corrected) pooled within-class covariance matrix and Wi the (corrected) within-class  covariance matrix of class i. The regularization is done by the two following successive steps (for each class i):

1. Continuum between QDA and LDA: Wi(1) = (1 - `alpha`) * Wi + `alpha` * W
2. Ridge regularization: Wi(2) = Wi(1) + `lb` * I

Then the QDA algorithm is run on matrices {Wi(2)}.

Function `rda` is slightly different from the regularization expression used by Friedman 1989 (Eq.18): the choice is  to shrink the covariance matrices Wi(2) to the diagonal of the Idendity matrix (ridge regularization; e.g. Guo  et al. 2007).  

Particular cases:

  * `alpha` = 1 & `lb` = 0 : LDA
  * `alpha` = 0 & `lb` = 0 : QDA
  * `alpha` = 1 & `lb` > 0 : Penalized LDA (Hastie et al 1995) with diagonal regularization matrix

See functions `lda` and `qda` for other details (arguments `weights`and `prior`).

## References

Friedman JH. Regularized Discriminant Analysis. Journal of the American Statistical Association. 1989;  84(405):165-175. doi:10.1080/01621459.1989.10478752.

Guo Y, Hastie T, Tibshirani R. Regularized linear discriminant analysis and its application in microarrays.  Biostatistics. 2007; 8(1):86-100. doi:10.1093/biostatistics/kxj035.

Hastie, T., Buja, A., Tibshirani, R., 1995. Penalized Discriminant Analysis. The Annals of Statistics 23, 73–102.

## Examples

```julia
using Jchemo, JchemoData, JLD2
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
ntrain = n - ntest
(ntot = n, ntrain, ntest)
tab(ytrain)
tab(ytest)

alpha = .5
lb = 1e-8
model = rda(; alpha, lb)
fit!(model, Xtrain, ytrain)
@names model
@names fitm = model.fitm
fitm.lev
fitm.ni

res = predict(model, Xtest) ;
@names res
@head res.posterior
@head res.pred
errp(res.pred, ytest)
conf(res.pred, ytest).cnt
```
