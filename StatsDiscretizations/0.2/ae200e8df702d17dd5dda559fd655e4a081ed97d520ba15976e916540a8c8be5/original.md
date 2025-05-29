```
RealLineDiscretizer{L, R, T, G <:AbstractVector{T}} <: AbstractRealLineDiscretizer{Interval{L, R, T}}
```

An extended continuous discretizer that partitions the real line into intervals based on a given grid of points. It extends the discretization beyond the grid by including intervals from -∞ to the first grid point and from the last grid point to +∞.

The type parameters `L` and `R` specify the endpoint types of the intervals (e.g., `Closed` or `Open`), `T` is the element type of the grid, and `G` is the type of the grid vector.

# Fields

  * `grid::G`: The grid of points used for discretization.

# Examples

```julia
grid = [0.0, 1.0, 2.0]
discr = RealLineDiscretizer{Closed,Open}(grid)
```
