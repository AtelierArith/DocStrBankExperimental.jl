```
prox_grad(x0, f, ∇f!, prox!; style=:noaccel, β=.5, ϵ=1e-7, max_iter=1000)
```

Minimize an objective function $f(x) + g(x)$, where $f(x)$ is differentibale while $g(x)$ is not, using the proximal gradient method.

#### Arguments

  * `x0::AbstractVector`    : initial parameter values (n x 1)
  * `f::Function`           : $f(x)$
  * `∇f!::Function`         : gradient of `f`
  * `prox!::Function`       : proximal operator of $g(x)$
  * `style::Symbol`         : acceleration style
  * `β::Real`               : line search parameter
  * `ϵ::Real`               : tolerance
  * `max_iter::Integer`     : max number of iterations

#### Returns

  * `x::AbstractVector` : minimizer (optimal parameter values) (n x 1)
