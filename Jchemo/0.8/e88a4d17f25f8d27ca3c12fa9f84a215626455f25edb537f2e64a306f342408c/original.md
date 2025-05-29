```
matB(X, y, weights::Weight)
```

Between-class covariance matrix.

  * `X` : X-data (n, p).
  * `y` : A vector (n) defining the class membership.
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Compute the between-class covariance matrix (output `B`)  of `X`. This is the (non-corrected) covariance matrix of  the weighted class centers.

## Examples

```julia
using Jchemo, StatsBase

n = 20 ; p = 3
X = rand(n, p)
y = rand(1:3, n)
tab(y) 
weights = mweight(ones(n)) 

res = matB(X, y, weights) ;
res.B
res.priors
res.ni
res.lev

res = matW(X, y, weights) ;
res.W
res.Wi

matW(X, y, weights).W + matB(X, y, weights).B
cov(X; corrected = false)

v = mweight(collect(1:n))
matW(X, y, v).priors 
matB(X, y, v).priors 
matW(X, y, v).W + matB(X, y, v).B
covm(X, v)
```
