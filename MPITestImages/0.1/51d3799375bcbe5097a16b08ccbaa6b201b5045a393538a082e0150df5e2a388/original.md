```julia
delta_image(
    size,
    numOfPoints;
    sizeOfPoint,
    distanceOfPoints,
    pivot,
    circularShape
)

```

Function to generate a phantom with discrete points. The `distanceOfPoints` argument takes two functions that take the number of the point to generate and return an integer. This makes the phantoms to generate highly customizable.

# Arguments

  * `size::Tuple{Integer, Integer}`: The size of the phantom
  * `numOfPoints::Integer`: The number of points to generate
  * `sizeOfPoint::Tuple{Integer, Integer}`: The size of the points in the phantom
  * `distanceOfPoints::Tuple{Function, Function}`: The distance to add between each points in x and y direction
  * `pivot::Tuple{Integer, Integer}`: The starting point to generate points towards (size, size)
  * `circularShape::Bool`: If true, points are generated as circular

# Examples

## Two simple dots

```jldoctest
julia> image = delta_image((8, 8), 2; sizeOfPoint=(3, 2), distanceOfPoints=(x -> 0, x -> 4), pivot=(3, 3))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  1.0  1.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```

## L-shaped arrangement

```jldoctest
julia> image = delta_image((8, 8), 3; sizeOfPoint=(2, 2), distanceOfPoints=(x -> x == 2 ? 3 : 0, x -> x == 3 ? -3 : 3), pivot=(3, 3))
8×8 Matrix{Float64}:
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0  1.0  1.0  0.0
 0.0  0.0  1.0  1.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
```
