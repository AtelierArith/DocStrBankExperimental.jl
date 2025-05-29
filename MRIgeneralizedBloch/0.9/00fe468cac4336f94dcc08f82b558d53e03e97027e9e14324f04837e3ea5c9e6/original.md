```
greens_superlorentzian(κ)
```

Evaluate the Green's function corresponding to a super-Lorentzian lineshape at `κ = (t-τ)/T2s`.

# Examples

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_superlorentzian((t-τ)/T2s)
0.1471246868094442
```
