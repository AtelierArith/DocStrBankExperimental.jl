```
auxquadgk(f::BatchIntegrand, a,b,c...; kws...)
```

Like [`auxquadgk`](@ref), but batches evaluation points for an in-place integrand to evaluate simultaneously. In particular, there are two differences from `quadgk`

1. The function `f.f!` should be of the form `f!(y, x) = y .= f.(x)`.  That is, it writes the return values of the integand `f(x)` in-place into its first argument `y`. (The return value of `f!` is ignored.) See [`BatchIntegrand`](@ref) for how to define the integrand.
2. `f.max_batch` must be large enough to contain `4*order+2` points to evaluate two Kronrod rules simultaneously. Choosing `max_batch=4*order+2` will reproduce the result of `quadgk`, however if `max_batch=n*(4*order+2)` up to `2n` Kronrod rules will be evaluated together, which can produce different results for integrands with multiple peaks when used together with relative tolerances. For an example see the manual
