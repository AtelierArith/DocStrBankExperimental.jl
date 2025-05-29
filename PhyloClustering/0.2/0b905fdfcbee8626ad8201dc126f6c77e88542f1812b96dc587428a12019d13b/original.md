```
distance(tree::AbstractMatrix{<:Real})
```

Get the distance Matrix of a tree Matrix returned by [`split_weight`](@ref).

# Arguments

  * `tree`: a B * N tree Matrix (each column of tree Matrix is a B-dimensional tree in bipartiton format).

# Output

A pairwise distance `Matrix` that can be the input of [`hc_label`](@ref).
