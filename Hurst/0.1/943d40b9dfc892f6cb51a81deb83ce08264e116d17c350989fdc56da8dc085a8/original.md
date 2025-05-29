```
generalised_hurst_exponent(X, τ_range, q)
```

Calculate the generalised Hurst exponent of the series `X` with absolute moment `q` over the range `τ_range` along with its standard error.

See also [`hurst_exponent`](@ref).

# Examples

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> generalised_hurst_exponent(X, 1:19, 0.5);
```
