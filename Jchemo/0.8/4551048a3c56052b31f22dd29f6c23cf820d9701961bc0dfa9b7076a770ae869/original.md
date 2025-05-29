```
kpca(; kwargs...)
kpca(X; kwargs...)
kpca(X, weights::Weight; kwargs...)
```

Kernel PCA  (Scholkopf et al. 1997, Scholkopf & Smola 2002, Tipping 2001).

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. principal components (PCs) to consider.
  * `kern` : Type of kernel used to compute the Gram matrices.   Possible values are: `:krbf`, `:kpol`. See respective    functions `krbf` and `kpol` for their keyword arguments.
  * `scal` : Boolean. If `true`, each column of `X` is scaled   by its uncorrected standard deviation.

The method is implemented by SVD factorization of the weighted  Gram matrix: 

  * D^(1/2) * Phi(X) * Phi(X)' * D^(1/2)

where X is the cenetred matrix and D is a diagonal matrix  of weights (`weights.w`) of the observations (rows of X).

## References

Scholkopf, B., Smola, A., MÃ¼ller, K.-R., 1997. Kernel principal  component analysis, in: Gerstner, W., Germond, A., Hasler,  M., Nicoud, J.-D. (Eds.), Artificial Neural Networks,  ICANN 97, Lecture Notes in Computer Science. Springer, Berlin,  Heidelberg, pp. 583-588. https://doi.org/10.1007/BFb0020217

Scholkopf, B., Smola, A.J., 2002. Learning with kernels: support  vector machines, regularization, optimization, and beyond, Adaptive  computation and machine learning. MIT Press, Cambridge, Mass.

Tipping, M.E., 2001. Sparse kernel principal component analysis.  Advances in neural information processing systems, MIT Press.  http://papers.nips.cc/paper/1791-sparse-kernel-principal-component-analysis.pdf

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
kern = :krbf ; gamma = 1e-4
model = kpca(; nlv, kern, gamma) ;
fit!(model, Xtrain)
@names model.fitm
@head T = model.fitm.T
T' * T
model.fitm.V' * model.fitm.V

@head Ttest = transf(model, Xtest)

res = summary(model) ;
@names res
res.explvarx
```
