```
dim_bottom(xs::Vector{T}, ys::Vector{S}; offset::S=0) -> Union{TopDimensions, BottomDimensions}
dim_bottom(object::Vector{Tuple{T, S}}; offset=zero(S)) where {T, S}
```

Computes the bottom dimension for a given set of x and y coordinates of an object.

# Arguments

  * `xs::Vector{T}`: A vector of x coordinates.
  * `ys::Vector{S}`: A vector of y coordinates.
  * `offset`: An optional offset value of type `S`. Defaults to zero.

# Returns

  * `HDimensions` object containing:

      * `x_dims`: The calculated x-dimensions.
      * `y_dims`: The adjusted y-dimensions.
      * `labels`: The dimension labels.
      * `minor_lines`: The minor lines for the dimensions.
      * `major_lines`: The major lines for the dimensions.
      * `offset`: offset from reference objects

If the offset is not provided, it is set to 10% of the range of x coordinates. The function then computes  the x and y dimensions, major and minor lines, and labels, and returns the  appropriate dimensions object based on the offset value.
