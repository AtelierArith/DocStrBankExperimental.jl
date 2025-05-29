```
create_matrix_templates(shapes::Vector{Vector{Int64}})
```

Creates a uniform, multidimensional template based on the specified shapes vector.

# Arguments

  * `shapes::Vector{Vector{Int64}}`: A vector of vectors, where each vector represent a dimension of the template to create.

# Returns

  * A vector of normalized arrays (uniform distributions), each having the multi-dimensional shape specified in the input vector.
