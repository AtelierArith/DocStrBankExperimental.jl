```
sum_region(
	integral_image_arr::AbstractArray,
	top_left::Tuple{Int,Int},
	bottom_right::Tuple{Int,Int}
) -> Number
```

# Arguments

  * `iA::IntegralArray{T, N}`: The intermediate Integral Image
  * `top_left::NTuple{N, Int}`: coordinates of the rectangle's top left corner
  * `bottom_right::NTuple{N, Int}`: coordinates of the rectangle's bottom right corner

# Returns

  * `sum::T` The sum of all pixels in the given rectangle defined by the parameters `top_left` and `bottom_right`
