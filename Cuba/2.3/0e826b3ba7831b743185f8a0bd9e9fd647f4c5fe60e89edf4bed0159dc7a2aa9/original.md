```
vegas(integrand, ndim=1, ncomp=1[, keywords]) -> integral, error, probability, neval, fail, nregions
```

Calculate integral of `integrand` over the unit hypercube in `ndim` dimensions using Vegas algorithm.  `integrand` is a vectorial function with `ncomp` components.  `ndim` and `ncomp` default to 1.

Accepted keywords:

  * `userdata`
  * `nvec`
  * `rtol`
  * `atol`
  * `flags`
  * `seed`
  * `minevals`
  * `maxevals`
  * `nstart`
  * `nincrease`
  * `nbatch`
  * `gridno`
  * `statefile`
  * `spin`
