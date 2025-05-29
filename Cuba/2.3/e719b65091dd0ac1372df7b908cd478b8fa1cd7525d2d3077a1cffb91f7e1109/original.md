```
cuhre(integrand, ndim=2, ncomp=1[, keywords]) -> integral, error, probability, neval, fail, nregions
```

Calculate integral of `integrand` over the unit hypercube in `ndim` dimensions using Cuhre algorithm.  `integrand` is a vectorial function with `ncomp` components.  `ncomp` defaults to 1, `ndim` defaults to 2 and must be ≥ 2.

Accepted keywords:

  * `userdata`
  * `nvec`
  * `rtol`
  * `atol`
  * `flags`
  * `minevals`
  * `maxevals`
  * `key`
  * `statefile`
  * `spin`
