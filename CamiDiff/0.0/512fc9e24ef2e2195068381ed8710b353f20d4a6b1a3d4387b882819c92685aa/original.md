```
grid_differentiation(f::Vector{T}, grid::Grid{T}; k=5) where T<:real
```

$k^{th}$-order lagrangian *derivative* of the function $f(r)$ over the range $0 ≤ r ≤ rmax$

  * `f[1:N]` : the function `f(r)` tabulated in forward order on a [`Grid`](@ref) of `N` points

#### Example:

```
julia> grid = castGrid(3, 1001, Float64; h=2π/1000.0, r0=1.0, msg=false);

julia> f = [sin(grid.r[i]) for i=1:grid.N]

julia> f′ = [cos(grid.r[i]) for i=1:grid.N]

julia> grid_differentiation(f, grid) ≈ f′
true
```

```
grid_differentiation(f::Vector{T}, grid::Grid{T}, rv::T, notation=fwd; k=5) where T<:Real
```

$k^{th}$-order lagrangian *derivative* of the function $f(r)$ at position `rv`

  * `f[1:N]` : the function `f(r)` tabulated in forward order on a [`Grid`](@ref) of `N` points
  * `fwd` using fwd-difference notation
  * `bwd` using bwd-difference notation

#### Example:

```
julia> grid = castGrid(3, 1001, Float64; h=2π/1000.0, r0=1.0, msg=false);

julia> f = [sin(grid.r[i]) for i=1:grid.N];

julia> grid_differentiation(f, grid, float(π), fwd) ≈ cos(π)
true
```

```
grid_differentiation(f::Vector{T}, grid::Grid{T}, n::Int, notation=fwd; k=5) where T<:Real
```

$k^{th}$-order lagrangian *derivative* of the function $f(r)$ at grid position `n`

  * `f[1:N]` : the function `f(r)` tabulated in forward order on a [`Grid`](@ref) of `N` points
  * `fwd` using fwd-difference notation
  * `bwd` using bwd-difference notation

#### Example:

```
julia> grid = castGrid(3, 1001, Float64; h=2π/1000.0, r0=1.0, msg=false);

julia> f = [sin(grid.r[i]) for i=1:grid.N];

julia> f′ = [cos(grid.r[i]) for i=1:grid.N];

julia> grid_differentiation(f, grid, 500, fwd) ≈ f′[500]
true
```

```
grid_differentiation(f::Vector{T}, grid::Grid{T}, n1::Int, n2::Int; k=5) where T<:Real
grid_differentiation(f::Vector{T}, grid::Grid{T}, itr::UnitRange; k=5) where T<:Real
```

$k^{th}$-order lagrangian *derivative* of the function $f(r)$ over the grid range `n1 ≤ n ≤ n2`

  * `f[1:N]` : the function `f(r)` tabulated in forward order on a [`Grid`](@ref) of `N` points
  * `n1=itr.start`, `n2=itr.stop`.
