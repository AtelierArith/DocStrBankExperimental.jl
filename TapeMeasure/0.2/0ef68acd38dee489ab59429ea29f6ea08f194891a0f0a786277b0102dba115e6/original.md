```
v_dim(objects::Vector{Vector{Tuple{T, S}}}; offset = zero(S)) where {T, S}
```

Calculate the vertical dimension of a collection of objects.

# Arguments

  * `objects::Vector{Vector{Tuple{T, S}}}`: A vector of vectors, where each inner vector contains tuples of type `(T, S)`.
  * `offset`: An optional offset value of type `S`. Defaults to `zero(S)`.

# Returns

  * `VDimensions` object containing:

      * `x_dims`: The x dimensions adjusted by the offset.
      * `y_dims`: The y dimensions.
      * `labels`: The dimension labels.
      * `minor_lines`: The minor lines for the dimensions.
      * `major_lines`: The major lines for the dimensions.
      * `offset`: offset from reference objects
