```
BatchIntegrand(f!, y::AbstractVector, [x::AbstractVector]; max_batch=typemax(Int))
BatchIntegrand{Y,X}(f!; max_batch=typemax(Int)) where {Y,X}
BatchIntegrand{Y}(f!; max_batch=typemax(Int)) where {Y}
```

Constructor for a `BatchIntegrand` accepting an integrand of the form `f!(y,x) = y .= f.(x)` that can evaluate the integrand at multiple quadrature nodes using, for example, threads, the GPU, or distributed memory. The arguments `y`, and optionally `x`, are pre-allocated buffers of the correct element type for the domain and range of `f!`. Additionally, they must be `resize!`-able since the number of evaluation points may vary between calls to `f!`. Alternatively, the element types of those buffers, `Y` and optionally `X`, may be passed as type parameters to the constructor. The `max_batch` keyword roughly limits the number of nodes passed to the integrand, though at least `4*order+2` nodes will be used by the GK rule.

## Internal allocations

If `x` or `X` are not specified, `quadgk` internally creates a new `BatchIntegrand` with the user-supplied `y` buffer and a freshly-allocated `x` buffer based on the domain types. So, if you want to reuse the `x` buffer between calls, supply `{Y,X}` or pass `y,x` explicitly.
