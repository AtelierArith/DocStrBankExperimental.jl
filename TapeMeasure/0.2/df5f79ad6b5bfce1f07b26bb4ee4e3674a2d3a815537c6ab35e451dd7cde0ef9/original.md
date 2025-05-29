```
h_dim(xs::Vector{Vector{T}}, ys::Vector{Vector{S}}; offset = zero(S)) where {T, S}
```

This function calculates the horizontal dimensions based on the input vectors `xs` and `ys`.

# Arguments

  * `xs::Vector{Vector{T}}`: A vector of vectors containing the x-coordinates.
  * `ys::Vector{Vector{S}}`: A vector of vectors containing the y-coordinates.
  * `offset`: An optional parameter with a default value of `zero(S)`, used to adjust the y-dimensions.

# Returns

  * `HDimensions` object containing:

      * `x_dims`: The calculated x-dimensions.
      * `y_dims`: The adjusted y-dimensions.
      * `labels`: The dimension labels.
      * `minor_lines`: The minor lines for the dimensions.
      * `major_lines`: The major lines for the dimensions.
      * `offset`: offset from reference objects
