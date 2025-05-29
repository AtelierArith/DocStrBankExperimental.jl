```
@polar (p)
```

Convert a tuple of two numbers to a Point of x, y Cartesian coordinates.

```julia
julia> @polar 10, pi/4
Point(7.0710678118654755, 7.071067811865475)
```

Example usage

```julia
@polar (10, pi/4)
@polar [10, pi/4]
@polar 10, pi/4
```
