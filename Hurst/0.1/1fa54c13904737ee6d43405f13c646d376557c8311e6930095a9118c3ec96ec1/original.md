```
generalised_hurst_range(X, τ_range, q_range)
```

Calculate the generalised Hurst exponent (GHE) of the series `X` with absolute moments `q_range` over the range `τ_range`, along with its standard error.

Returns a `(length(q_range), 2)` matrix where the first column contains the values of the GHE and the second column contains the standard errors.

See also [`hurst_exponent`](@ref).

# Examples

```jldoctest
julia> X = accumulate(+, randn(1000));

julia> q_range = 0.:0.1:1.; tau_range = 1:19;

julia> generalised_hurst_range(X, tau_range, q_range);
```
