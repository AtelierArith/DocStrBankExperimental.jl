```
auxquadgk!(f!, result, a,b,c...; rtol=sqrt(eps), atol=0, maxevals=10^7, order=7, norm=norm)
```

Like [`auxquadgk`](@ref), but make use of in-place operations for array-valued integrands (or other mutable types supporting in-place operations).  In particular, there are two differences from `quadgk`:

1. The function `f!` should be of the form `f!(y, x) = y .= f(x)`.  That is, it writes the return value of the integand `f(x)` in-place into its first argument `y`.   (The return value of `f!` is ignored.)
2. Like `auxquadgk`, the return value is a tuple `(I,E)` of the estimated integral `I` and the estimated error `E`.   However, in `auxquadgk!` the estimated integral is written in-place into the `result` argument, so that `I === result`.

Otherwise, the behavior is identical to `auxquadgk`.

For integrands whose values are *small* arrays whose length is known at compile-time, it is usually more efficient to use `quadgk` and modify your integrand to return an `SVector` from the [StaticArrays.jl package](https://github.com/JuliaArrays/StaticArrays.jl).
