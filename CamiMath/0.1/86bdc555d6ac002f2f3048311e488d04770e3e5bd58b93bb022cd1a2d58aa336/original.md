```
lagrange_polynom(f::Vector{T}, start::Int, stop::Int [, sense=fwd]) where T<:Real
lagrange_polynom(f::Vector{T}, itr::UnitRange [, sense=fwd]) where T<:Real
```

The coefficients of the [`polynomial`](@ref) of degree $d =$`stop`-`start` running  through $d+1$ subsequent points of the tabulated regular function $f[n]$.  For `sense` = [`fwd](@ref) these are the points $f[n:n+d]$, for `sense` = [`bwd`](@ref)  the points $f[n-k:n]$. The corresponding [`polynomial`](@ref) is most accurate near $f[n]$. 

#### Examples:

```
julia> a = [0.0, 1.0, 4.0, 9.0, 16.0, 25.0];

julia> polynom = lagrange_polynom(a, 1, 4, fwd); println(polynom)
[0.0, 0.0, 1.0, 0.0]

julia> f(x) = polynomial(polynom, x); 

julia> f(0.0), f(0.5), f(1.0), f(2.0), f(3.0)
(0.0, 0.25, 1.0, 4.0, 9.0)

julia> polynom = lagrange_polynom(a, 1:4, bwd); println(polynom)
[9.0, 6.0, 1.0, -4.440892098500626e-16]

julia> f(x) = polynomial(polynom, x); 

julia> f(-3.0), f(-2.5), f(-2.0), f(-1.0), f(0.0)
(1.199040866595169e-14, 0.25000000000000694, 1.0000000000000036, 4.0, 9.0)
```
