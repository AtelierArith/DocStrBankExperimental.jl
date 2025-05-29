A general type for holding multi-dimensional data (usually a matrix) along with associated dimension bounds. It's main purpose is to handle the conversion between world coordinates and grid indices internally. Converting between the two representations treats rows as the first variable (x-axis), columns as the second (y-axis), and so on.

Its typical use is to act as a 2D map of some value that can be sampled. A GridMap will return the value of the grid cell that a given point falls within. In other words, the map value is constant within each cell. One can also think of this as a nearest-neighbor approximation.

Each cell index is treated as the center of its cell. Thus the map's lower bounds are at the center of the first cell and the map's upper bounds are at the center of the last cell.

Also made to function directly like a built-in N-dimensional array by sub-typing and implementing the base methods.

Fields:

  * `data::AbstractArray`: N-dimensional array of data
  * `bounds::@NamedTuple{lower::Vector{Float64}, upper::Vector{Float64}}`: vectors of lower and upper bounds, defaults to zeros and ones

A GridMap is constructed by passing the multi-dimensional array of data and the dimension bounds. If no bounds are passed, they default to zeros for lower and ones for upper.

# Examples

```julia
data = reshape(1:25, 5, 5)
bounds = (
    lower = [0.0, 0.0],
    upper = [1.0, 1.0]
)
gmap = GridMap(data, bounds)
gmap2 = GridMap(data) # bounds will be zero to one
```
