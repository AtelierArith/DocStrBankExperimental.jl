```
standardize_tree(tree::AbstractMatrix{<:Real})
```

Standardize tree Matrix that returned by [`split_weight`](@ref).  It is recommended to standardize the data before inputting it into the model.

# Arguments

  * `tree`: a N * B Matrix containing trees (each row is a B-dimensional tree in bipartiton format).

# Output

A standardized B * N tree `Matrix` with a mean of about 0 and a standard deviation of about 1.     This tree `Matrix` can be the input of [model](@ref basics).
