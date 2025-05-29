```
MinimumDistance{T}
```

The lists of minimum-distances are stored in arrays of type `Vector{MinimumDistance{T}}`. The index of this vector corresponds to the index of the molecule in the original array.

`MinimumDistance{T}` is a simple structure that contains four fields: a boolean marker indicating if the distance is within the cutoff, the indexes `i` and `j` of the atoms of the  molecules that are closer to each other, and the distance `d`, with type `T`, which is the same as that of the coordinates of the input vectors of coordinates.

## Example

```julia-repl
julia> md = MinimumDistance{Float32}(true, 2, 5, 1.f0)
MinimumDistance{Float32}(true, 2, 5, 1.0f0)

julia> md.i
2

julia> md.j
5

julia> md.d
1.0f0
```
