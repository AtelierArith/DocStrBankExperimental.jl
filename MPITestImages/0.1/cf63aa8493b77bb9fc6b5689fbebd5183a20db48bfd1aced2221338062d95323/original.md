```julia
checker_image()
checker_image(size)
checker_image(size, checkersCount)
checker_image(size, checkersCount, stripeWidth)

```

Function to generate a phantom with a checker board pattern. This function uses a best effort approach, meaning that it is tried to cover most of the phantom with the pattern using the specified parameters.

# Arguments

  * `size::Tuple{Integer, Integer}`: The size of the phantom
  * `checkersCount::Tuple{Integer, Integer}`: How many squares to generate along each axis
  * `stripeWidth::Tuple{Integer, Integer}`: By default `(1, 1)`. Sets the width of the lines between the squares

# Examples

```jldoctest
julia> image = checker_image((8, 8), (2, 3), (2, 1))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  1.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  1.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
