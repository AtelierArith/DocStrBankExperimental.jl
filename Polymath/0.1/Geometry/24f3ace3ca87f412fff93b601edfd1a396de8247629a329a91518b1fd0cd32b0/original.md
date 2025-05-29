```
has_euler_characteristic(edges, faces, vertices)
```

Determine whether or not a polyhedron has the Euler characteristic given the edges, faces, and vertices.

# Examples

```julia-repl
julia> has_euler_characteristic(6, 4, 4) # tetrahedron
true

julia> has_euler_characteristic(12, 7, 6) # tetrahemihexahedron
false
```
