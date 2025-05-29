```
fracPos(n::Int, rval::T, grid::Grid{T}; ϵ = 1e-8, k = 7) where T<:Real
```

Fractional grid offset with respect to [`Grid`](@ref) position `n`.

#### Example:

Consider the exponential grid of 4 points defined by 

```
julia> grid = castGrid("exponential", 4, Float64; h = 0.1, rmax = 2.0);

julia> println(grid.r)
[0.0, 0.6012192107114549, 1.265669197778149, 2.0]
```

The point $r = 1.0$ is located just above $n = 2$,  with fractional position $Δn = 0.6120806373655796$.

```
julia> r = 1.0;

julia> n = gridPos(r, grid)
2

julia> Δn = fracPos(n, r, grid);

julia> t = (n+Δn-1)*grid.h;

julia> grid.r0 * (exp(t)-1) ≈ r
```
