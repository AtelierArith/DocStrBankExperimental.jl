```
enum_linear_regions_rat(f::TropicalPuiseuxPoly, g::TropicalPuiseuxPoly, verbose)
```

Computes the linear regions of a tropical Puiseux rational function f/g Inputs: Tropical Puiseux polynomials f and g Ouput: array containing linear regions of f/g represented by polyhedra/arrays of polyhedra.

# Example

Enumerates the linear regions of f/g where f = max(x, y) and g = max(x+y, x+2y).

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> g = TropicalPuiseuxPoly(Dict([1, 1] => 0, [1, 2] => 0), [[1, 1], [1, 2]]);

julia> enum_linear_regions_rat(f, g)
4-element Vector{Any}:
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
 Polyhedron in ambient dimension 2 with Float64 type coefficients
```
