```
interpolate_greens_function(f, κmin, κmax)
```

Interpolate the Green's function f in the range between κmin and κmax.

The interpolation uses the ApproxFun.jl package that incorporates Chebyshev polynomials and ensures an approximation to machine precision.

# Examples

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> greens_superlorentzian((t-τ)/T2s)
0.1471246868094442

julia> Gint = interpolate_greens_function(greens_superlorentzian, 0, 20);


julia> Gint((t-τ)/T2s)
0.14712468680944407
```
