```
maxmin(atoms::AbstractVector{<:Atom}; selection)
```

Returns the maximum and minimum coordinates of an atom vector, and the length (maximum minus minimum) in each direction. 

### Example

```julia-repl
julia> protein = wget("1LBD");

julia> maxmin(protein)
 
 Minimum atom coordinates: xmin = [-29.301, 57.178, 45.668]
 Maximum atom coordinates: xmax = [47.147, 99.383, 86.886]
 Length in each direction: xlength = [76.448, 42.205, 41.217999999999996]

```
