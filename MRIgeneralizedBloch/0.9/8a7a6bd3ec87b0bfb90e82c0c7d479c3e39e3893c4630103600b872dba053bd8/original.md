```
greens_gaussian(κ)
```

Evaluate the Green's function corresponding to a Gaussian lineshape at `κ = (t-τ)/T2s`.

# Examples

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_gaussian((t-τ)/T2s)
1.9287498479639178e-22
```
