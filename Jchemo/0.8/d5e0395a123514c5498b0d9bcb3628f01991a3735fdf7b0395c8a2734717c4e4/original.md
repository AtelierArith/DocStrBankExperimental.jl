```
rp(; kwargs...)
rp(X; kwargs...)
rp(X, weights::Weight; kwargs...)
rp!(X::Matrix, weights::Weight; kwargs...)
```

Make a random projection of X-data.

  * `X` : X-data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Keyword arguments:

  * `nlv` : Nb. dimensions on which `X` is projected.
  * `meth` : Method of random projection. Possible   values are: `:gauss`, `:li`. See the respective    functions `rpmatgauss` and `rpmatli` for their    keyword arguments.
  * `scal` : Boolean. If `true`, each column of `X`    is scaled by its uncorrected standard deviation.

## Examples

```julia
using Jchemo
n, p = (5, 10)
X = rand(n, p)
nlv = 3
meth = :li ; s = sqrt(p) 
#meth = :gauss
model = rp(; nlv, meth, s)
fit!(model, X)
@names model
@names model.fitm
@head model.fitm.T 
@head model.fitm.V 
transf(model, X[1:2, :])
```
