```
findslices(scorer, path::EinExpr; size, slices, overhead, temperature = 0.01, skip = head(path))
```

Search for indices to be cut/sliced such that the conditions given by `size`, `overhead` and `slices` are fulfilled. Reimplementation based on [`contengra`](https://github.com/jcmgray/cotengra)'s `SliceFinder` algorithm.

# Arguments

  * `scorer` Heuristic function (or functor) that accepts a path and a candidate index for cutting, and returns a score.
  * `path` The contraction path target for tensor cutting aka slicing.

# Keyword Arguments

  * `size` If specified, the largest intermediate tensor of the slice won't surpass this size (in number of elements).
  * `slices` If specified, there will be at least `slices` different slices when cutting all returnt indices.
  * `overhead` If specified, the amount of redundant operations between a slice and the original contraction won't supass this ratio.
  * `temperature` Temperature of the Boltzmann-like noise added for diffusing results.
  * `skip` Indices not to be considered for slicing.
