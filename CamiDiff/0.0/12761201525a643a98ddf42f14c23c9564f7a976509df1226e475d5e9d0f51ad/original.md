```
gridPos(rval::T, grid::Grid{T}) where T<:Number
```

The approximate grid position defined as the largest integer `n` satisfying the  condition `grid.r[n] < rval` on the [`Grid`](@ref).

#### Example:

Consider the exponential grid of 4 points defined by 

```
julia> grid = castGrid("exponential", 4, Float64; h = 0.1, rmax = 2.0);

julia> println(grid.r)
[0.0, 0.6012192107114549, 1.265669197778149, 2.0]
```

The approximate grid position of the point $r = 1.0$ is $2$ ($n = 2$); i.e., $r = 1.0$ is larger than $0.6012192107114549$ ($n = 2$) but smaller than  $1.265669197778149$ ($n = 3$).

```
julia> r = 1.0;

julia> n = gridPos(r, grid)
2
```
