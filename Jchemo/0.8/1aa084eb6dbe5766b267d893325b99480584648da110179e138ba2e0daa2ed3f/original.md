```
spca(; kwargs...)
spca(X; kwargs...)
spca(X, weights::Weight; kwargs...)
spca!(X::Matrix, weights::Weight; kwargs...)
```

Sparse PCA (Shen & Huang 2008).

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. principal components (PCs).
  * `meth` : Method used for the sparse thresholding.    Possible values are: `:soft`, `:hard`. See thereafter.
  * `nvar` : Nb. variables (`X`-columns) selected for each principal   component (PC). Can be a single integer (i.e. same nb.    of variables for each PC), or a vector of length `nlv`.
  * `defl` : Type of `X`-matrix deflation, see below.
  * `tol` : Tolerance value for stopping the Nipals iterations.
  * `maxit` : Maximum nb. of Nipals iterations.
  * `scal` : Boolean. If `true`, each column of `X` is scaled   by its uncorrected standard deviation.

sPCA-rSVD algorithm (regularized low rank matrix approximation) of  Shen & Huang 2008. 

The algorithm computes each loadings vector iteratively, by alternating  least squares regressions (Nipals) including a step of thresholding. Function  `spca` provides thresholding methods '1' and '2' reported in Shen & Huang 2008  Lemma 2 (`:soft` and `:hard`):

  * The tuning parameter used by Shen & Huang 2008 is the number of null elements    in the loadings vector, referred to as degree of sparsity. Conversely, the    present function `spca` uses the number of non-zero elements (`nvar`),    equal to p - degree of sparsity.
  * See the code of function `snipals_shen` for details on how is computed    the cutoff 'lambda' used inside the thresholding function (Shen & Huang 2008),    given a value for `nvar`. Differences from other softwares may occur    when there are tied values in the loadings vector (depending on the choices    of method used to compute quantiles).

Matrix `X` can be deflated in two ways:

  * `defl = :v` : Matrix `X` is deflated by regression of the `X'`-columns on  the loadings vector `v`. This is the method proposed by Shen & Huang 2008  (see in Theorem A.2 p.1033).
  * `defl = :t` : Matrix `X` is deflated by regression of the `X`-columns on  the score vector `t`. This is the method used in function `spca` of the  R package `mixOmics` (Le Cao et al. 2016).

The method of computation of the % variance explained in X by each PC (returned  by function `summary`) depends on the type of deflation chosen (see the code).    

## References

Kim-Anh Lê Cao, Florian Rohart, Ignacio Gonzalez, Sebastien  Dejean with key contributors Benoit Gautier, Francois Bartolo,  contributions from Pierre Monget, Jeff Coquery, FangZou Yao  and Benoit Liquet. (2016). mixOmics: Omics Data Integration  Project. R package version 6.1.1.  https://www.bioconductor.org/packages/release/bioc/html/mixOmics.html

Shen, H., Huang, J.Z., 2008. Sparse principal component  analysis via regularized low rank matrix approximation.  Journal of Multivariate Analysis 99, 1015–1034.  https://doi.org/10.1016/j.jmva.2007.06.007

## Examples

```julia
using Jchemo, JchemoData, JLD2 
path_jdat = dirname(dirname(pathof(JchemoData)))
db = joinpath(path_jdat, "data/iris.jld2") 
@load db dat
@names dat
@head dat.X
X = dat.X[:, 1:4]
n = nro(X)
ntest = 30
s = samprand(n, ntest) 
Xtrain = X[s.train, :]
Xtest = X[s.test, :]

nlv = 3 
meth = :soft
#meth = :hard
nvar = 2
model = spca(; nlv, meth, nvar) ;
fit!(model, Xtrain) 
fitm = model.fitm ;
@names fitm
fitm.niter
fitm.sellv 
fitm.sel
V = fitm.V
V' * V
@head T = fitm.T
T' * T
@head transf(model, Xtrain)

@head Ttest = transf(fitm, Xtest)

res = summary(model, Xtrain) ;
res.explvarx
```
