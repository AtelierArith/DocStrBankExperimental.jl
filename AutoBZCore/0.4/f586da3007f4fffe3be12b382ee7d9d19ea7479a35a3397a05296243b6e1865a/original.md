```
QuadratureFunction(; fun=trapz, npt=50, nthreads=1)
```

Quadrature rule for the standard interval [-1,1] computed from a function `x, w = fun(npt)`. The nodes and weights should be set so the integral of `f` on [-1,1] is `sum(w .* f.(x))`. The default quadrature rule is [`trapz`](@ref), although other packages provide rules, e.g.

```
using FastGaussQuadrature
alg = QuadratureFunction(fun=gausslegendre, npt=100)
```

`nthreads` sets the numbers of threads used to parallelize the quadrature only when the integrand is a , in which case the user must parallelize the integrand evaluations. For no threading set `nthreads=1`.
