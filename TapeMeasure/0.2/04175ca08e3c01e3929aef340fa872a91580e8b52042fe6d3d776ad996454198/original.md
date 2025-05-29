```
v_dim(xs::Vector{Vector{T}}, ys::Vector{Vector{S}}; offset = zero(T)) where {T, S}
```

Calculate the vertical dimensions for a given set of x and y coordinates.

# Arguments

  * `xs::Vector{Vector{T}}`: A vector of vectors containing the x coordinates.
  * `ys::Vector{Vector{S}}`: A vector of vectors containing the y coordinates.
  * `offset`: An optional parameter with a default value of `zero(S)`, used to adjust the x-dimensions.

# Returns

  * `VDimensions` object containing:

      * `x_dims`: The x dimensions adjusted by the offset.
      * `y_dims`: The y dimensions.
      * `labels`: The dimension labels.
      * `minor_lines`: The minor lines for the dimensions.
      * `major_lines`: The major lines for the dimensions.
      * `offset`: offset from reference objects
