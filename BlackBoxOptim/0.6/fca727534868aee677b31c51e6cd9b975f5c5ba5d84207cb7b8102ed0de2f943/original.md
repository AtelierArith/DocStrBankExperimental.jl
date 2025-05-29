```
rand_individuals(ss, n; [method=:latin_hypercube])
```

Generate `n` individuals by randomly sampling in the `ss` search space using specified sampling `method`. The supported methods are:

  * `uniform`: uniform independent sampling for each dimension
  * `latin_hypercube` (the default): use latin hypercube sampling method
