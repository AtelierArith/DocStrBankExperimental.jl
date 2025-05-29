```
polyhedron(f::TropicalPuiseuxPoly, i::Int)
```

Ouputs the polyhedron corresponding to points where f is given by the  linear map corresponding to the i-th monomial of f. 

# Example

Output the polyhedron where f = max(x, y) is equal to x

```jldoctest
julia> f = TropicalPuiseuxPoly(Dict([1, 0] => 0, [0, 1] => 0), [[1, 0], [0, 1]]);

julia> polyhedron(f, [1, 0])
Polyhedron in ambient dimension 2 with Float64 type coefficients
```
