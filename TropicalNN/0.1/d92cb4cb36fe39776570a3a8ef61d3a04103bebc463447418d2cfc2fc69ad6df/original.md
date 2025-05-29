```
enum_linear_regions(f::TropicalPuiseuxPoly)
```

Outputs an array of tuples (poly, bool) indexed by the same set as the exponents of f. The tuple element poly  is the linear region corresponding to the exponent, and bool is true when this region is nonemtpy.

# Example

Enumerates the linear regions of f = max(x, y).

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> enum_linear_regions(f)
2-element Vector{Any}:
 (Polyhedron in ambient dimension 2 with Float64 type coefficients, true)
 (Polyhedron in ambient dimension 2 with Float64 type coefficients, true)
```
