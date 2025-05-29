```
toarray(ss::SquareSet, T::Type{<:Number}=Float32)
```

Convert a square set to a two-dimensional array of the specified element type.

The returned array's columns corresponds to the files, and the rows to the ranks. The array entries are 1 for the members of the square set, and 0 for non-members.

# Examples

```julia-repl
julia> toarray(SS_FILE_C ∪ SS_RANK_5, Int)
8×8 Array{Int64,2}:
 0  0  1  0  0  0  0  0
 0  0  1  0  0  0  0  0
 0  0  1  0  0  0  0  0
 1  1  1  1  1  1  1  1
 0  0  1  0  0  0  0  0
 0  0  1  0  0  0  0  0
 0  0  1  0  0  0  0  0
 0  0  1  0  0  0  0  0
```
