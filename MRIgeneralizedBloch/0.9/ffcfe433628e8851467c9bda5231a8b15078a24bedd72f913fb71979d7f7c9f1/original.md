```
greens_lorentzian(κ)
```

Evaluate the Green's function corresponding to a Lorentzian lineshape at `κ = (t-τ)/T2s`.

# Examples

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_lorentzian((t-τ)/T2s)
4.5399929762484854e-5
```
