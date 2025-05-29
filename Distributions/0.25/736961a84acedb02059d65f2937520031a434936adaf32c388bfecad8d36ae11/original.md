```
logpdf!(out, d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

Evaluate the logarithm of the probability density function of `d` at every element in a collection `x` and save the results in `out`.

This function checks if the size of `out` is compatible with `d` and `x` and for every element of `x` if its size is compatible with distribution `d`. These checks can be disabled by using `@inbounds`.

Here, `x` can be

  * an array of dimension `> N` with `size(x)[1:N] == size(d)`, or
  * an array of arrays `xi` of dimension `N` with `size(xi) == size(d)`.

# Implementation

Instead of `logpdf!` one should implement `_logpdf!(out, d, x)` which does not have to check the size of `out` and `x`.

See also: [`pdf!`](@ref).
