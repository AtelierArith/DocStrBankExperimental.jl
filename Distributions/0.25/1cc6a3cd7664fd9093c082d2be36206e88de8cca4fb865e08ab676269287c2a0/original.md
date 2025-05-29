```
pdf!(out, d::Distribution{ArrayLikeVariate{N}}, x) where {N}
```

Evaluate the probability density function of `d` at every element in a collection `x` and save the results in `out`.

This function checks if the size of `out` is compatible with `d` and `x` and for every element of `x` if its size is compatible with distribution `d`. These checks can be disabled by using `@inbounds`.

Here, `x` can be

  * an array of dimension `> N` with `size(x)[1:N] == size(d)`, or
  * an array of arrays `xi` of dimension `N` with `size(xi) == size(d)`.

# Implementation

Instead of `pdf!` one should implement `_pdf!(out, d, x)` which does not have to check the size of `out` and `x`. However, since the default definition of `_pdf!(out, d, x)` falls back to `logpdf!` usually it is sufficient to implement `logpdf!`.

See also: [`logpdf!`](@ref).
