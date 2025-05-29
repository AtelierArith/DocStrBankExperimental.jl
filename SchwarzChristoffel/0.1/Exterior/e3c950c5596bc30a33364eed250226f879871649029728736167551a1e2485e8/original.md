```
coefficients(m::ConformalMap) -> Tuple{Vector{ComplexF64},Vector{ComplexF64}}
```

Returns a tuple of vectors of the complex coefficients of the multipole expansion of the mapping $z(\zeta)$ described by `m` as well as the coefficients of the square magnitude of the mapping $|z(\zeta)|^2$.

# Example

```jldoctest
julia> p = Polygon([-1.0,0.2,1.0,-1.0],[-1.0,-1.0,0.5,1.0]);

julia> m = ExteriorMap(p);

julia> ccoeff, dcoeff = coefficients(m);
```
