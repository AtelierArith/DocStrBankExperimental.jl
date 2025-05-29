```
grid_integration(f::Vector{T}, grid::Grid{T}) where T<:Real
grid_integration(f::Vector{T}, grid::Grid{T}, n1::Int, n2::Int) where T<:Real
grid_integration(f::Vector{T}, grid::Grid{T}, itr::UnitRange) where T<:Real
```

Integral of the analytic function $f(r)$ tabulated on a generally nonlinear  [`Grid`](@ref) and evaluated with the generalized trapezoidal rule optimized  with endpoint correction by the weightsvector `grid.epw`,

$$
    ∫_{0}^{r_n} f(r) dr = ∫_{0}^{n} f(x) r^{\prime}(x) dx.
$$

Here, the latter integral corresponds to the optimized trapezoidal rule for a uniform grid (see [`trapezoidal_integration`](@ref)). The rule is exact for polynomial functions of degree $d=0,\ 1,⋯\ k-1$, where $k=$ `grid.epn`. For $k=1$ the rule reduces to the ordinary trapezoidal rule (weights = [1/2]).

#### Examples:

```
julia> ftest(r) = sqrt(2.0/π) * exp(-r^2/2.0);

julia> grid1 = castGrid(1, 1000, Float64; h = 0.005, r0 = 0.1, msg=true);
Grid created: exponential, Float64, rmax = 14.7413, N = 1000, h = 0.005, r0 = 0.1

julia> grid2 = castGrid(2, 1000, Float64; h = 0.005, r0 = 0.1, p=5, msg=true);
Grid created: truncated-exponential, Float64, rmax = 9.04167, N = 1000, p = 5, h = 0.005, r0 = 0.1

julia> grid3 = castGrid(3, 1000, Float64; h = 0.1, r0 = 0.1, msg=true);
Grid created: linear (uniform), Float64, rmax = 10.0, N = 1000, p = 1, h = 0.1, r0 = 0.1

julia> grid4 = castGrid(4, 1000, Float64; h = 0.1, r0 = 0.001, polynom=[0,0,1], msg=true);
Grid created: polynomial, Float64, rmax = 10.0, N = 1000, polynom = [0.0, 0.0, 1.0], h = 0.1, r0 = 0.001

julia> r1 = grid1.r;
julia> r2 = grid2.r;
julia> r3 = grid3.r;
julia> r4 = grid4.r;
julia> f1 = [ftest(r1[n]) for n=1:grid1.N];
julia> f2 = [ftest(r2[n]) for n=1:grid2.N];
julia> f3 = [ftest(r3[n]) for n=1:grid3.N];
julia> f4 = [ftest(r4[n]) for n=1:grid4.N];
julia> o1 = grid_integration(f1, grid1);
julia> o2 = grid_integration(f2, grid2);
julia> o3 = grid_integration(f3, grid3, 1:900);
julia> o4 = grid_integration(f4, grid4, 1:900);

julia> println("integral on " * grid1.name * " grid = ", o1)
integral on exponential grid = 1.0

julia> println("integral on " * grid2.name * " grid = ", o2)
integral on truncated-exponential grid: 1.0

julia> println("integral on " * grid3.name * " grid = ", o3)
integral on linear (uniform) grid = 1.000000000000003

julia> println("integral on " * grid3.name * " grid = ", o4)
integral on polynomial grid = 1.0000000000000013
```
