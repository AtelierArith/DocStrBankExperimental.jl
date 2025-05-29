```
elementmps(A, el...)
```

Return the element of the MPS `A` for the set of physical states `el...`

# Examples

```julia-repl
julia> A = chainmps(6, [2,4], 1);

julia> elementmps(A, 1, 2, 1, 1, 1, 1)
0.7071067811865475

julia> elementmps(A, 1, 1, 1, 2, 1, 1)
0.7071067811865475

julia> elementmps(A, 1, 2, 1, 2, 1, 1)
0.0

julia> elementmps(A, 1, 1, 1, 1, 1, 1)
0.0
```
