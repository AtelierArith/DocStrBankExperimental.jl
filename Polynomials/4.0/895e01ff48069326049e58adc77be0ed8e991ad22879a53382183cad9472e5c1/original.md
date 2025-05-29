```
poles(pq::AbstractRationalFunction{T};
    method=:numerical, multroot_method=nothing, kwargs...) where {T}
```

For a rational function `p/q`, first reduces to normal form, then finds the roots and multiplicities of the resulting denominator.

  * `method` is used to pass to `lowest_terms`
  * `multroot_method` is passed to the method argument of `multroot`, which can be `:direct` (the faster default) or `:iterative` (the slower, and possibly more robust alternate). The default is `:direct` save for `Big` values in which case `:iterative` is used.
