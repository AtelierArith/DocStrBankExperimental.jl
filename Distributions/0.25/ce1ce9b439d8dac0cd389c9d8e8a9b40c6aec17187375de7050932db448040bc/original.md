```
loglikelihood(d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

The log-likelihood of distribution `d` with respect to all variate(s) contained in `x`.

Here, `x` can be any output of `rand(d, dims...)` and `rand!(d, x)`. For instance, `x` can be

  * an array of dimension `N` with `size(x) == size(d)`,
  * an array of dimension `N + 1` with `size(x)[1:N] == size(d)`, or
  * an array of arrays `xi` of dimension `N` with `size(xi) == size(d)`.
