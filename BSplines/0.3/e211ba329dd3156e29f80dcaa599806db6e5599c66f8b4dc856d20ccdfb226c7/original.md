```
splinevalue(spline::Spline, x[, ::Derivative{N}]; kwargs...)
```

Calculate the value of `spline`, or its `N`-th derivative, at `x`.

Two optional keyword arguments can be used to increase performance:

  * `workspace`: By default, the function allocates a vector of length `order(spline)` in which the calculation is performed. To avoid this, a pre-allocated vector can be supplied with the `workspace` keyword. In this case, the returned value is always of type `eltype(workspace)`.
  * `leftknot`: If the index of the relevant interval (i.e., `intervalindex(basis(spline), x)`) is already known, it can be supplied with the `leftknot` keyword.

Instead of calling `splinevalue`, a spline object can be called directly: `spline(x[, Derivative(N)]; kwargs...)` is equivalent to `splinevalue(spline, x[, Derivative(N)]; kwargs...)`.

# Examples

```jldoctest
julia> spl = Spline(BSplineBasis(4, 0:5), 1:8);

julia> splinevalue(spl, 1.7)
3.69775

julia> splinevalue(spl, 1.7, Derivative(1))
1.0225

julia> splinevalue(spl, 3.6, leftknot=7)
5.618

julia> spl(18//5)
2809//500

julia> spl(3.6, Derivative(3), leftknot=7)
0.5
```
