```
grid_interpolation(f::Vector{T}, grid::Grid{T}, rv::T, notation=fwd; k=5) where T<:Real
```

$$
k^{th}
$$

-order lagrangian *補間* of the function $f(r)$ at position `r` 

  * `f[1:N]` : the function `f(r)` tabulated in forward order on a [`Grid`](@ref) of `N` points
  * `fwd` using fwd-difference notation
  * `bwd` using bwd-difference notation

#### 例:

```
julia> grid = castGrid(1, 1000, Float64; h = 0.01, rmax=25, msg=false);

julia> r = grid.r;

julia> f = [exp(-r[n]) for n=1:grid.N];

julia> rv = 1.0;

julia> grid_interpolation(f, grid, rv, fwd) ≈ exp(-rv)
true
```
