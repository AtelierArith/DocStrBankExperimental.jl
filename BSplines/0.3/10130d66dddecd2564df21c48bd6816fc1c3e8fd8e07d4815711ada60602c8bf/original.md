```
bsplines(basis, x[, derivative]; kwargs...)
```

Calculate the values and/or derivatives of all non-zero B-splines of `basis` at `x`.

If all B-splines of `basis` are zero at `x`, `nothing` is returned. If any B-splines are non-zero at `x`, an `OffsetArray` is returned. Its size and contents depend on the optional `derivative` argument:

  * If `derivative` is not given, the returned `OffsetArray` contains the value of the `i`-th B-spline at the index `i`.
  * If `derivative == Derivative(N)`, the returned `OffsetArray` contains the `N`-th derivative of the `i`-th B-spline at the index `i`.
  * If `derivative == AllDerivatives(N)`, the returned `OffsetArray` contains the `m`-th derivative (`0 ≤ m < N`) of the `i`-th B-spline at the index `i, m`.

Two optional keyword arguments can be used to increase performance:

  * `derivspace`: When calculating derivatives, some coefficients are stored in a matrix of size `(order(basis), order(basis))`. By default, the function allocates a new matrix. To avoid this, a pre-allocated matrix can be supplied with the `derivspace` keyword. It can only be used when calculating derivatives, i.e., with `Derivative(N)` where `N ≥ 1` or `AllDerivatives(N)` where `N ≥ 2`. To also pre-allocate the array that contains the result, use the [`bsplines!`](@ref) function instead.
  * `leftknot`: If the index of the relevant interval (i.e., `intervalindex(basis(spline), x)`) is already known, it can be supplied with the `leftknot` keyword.

# Examples

```jldoctest
julia> basis = BSplineBasis(4, 0:5);

julia> bsplines(basis, 2.4)
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 0.03600000000000002
 0.5386666666666667
 0.41466666666666663
 0.01066666666666666

julia> bsplines(basis, 2.4, Derivative(1), derivspace=zeros(4,4))
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 -0.18000000000000005
 -0.5599999999999999
  0.66
  0.07999999999999996

julia> bsplines(basis, 6) # returns nothing

julia> bsplines(basis, 17//5, leftknot=7)
4-element OffsetArray(::Vector{Rational{Int64}}, 4:7) with eltype Rational{Int64} with indices 4:7:
   9//250
 202//375
 307//750
   2//125

julia> bsplines(basis, 2.4, AllDerivatives(3))
4×3 OffsetArray(::Matrix{Float64}, 3:6, 0:2) with eltype Float64 with indices 3:6×0:2:
 0.036      -0.18   0.6
 0.538667   -0.56  -0.8
 0.414667    0.66  -0.2
 0.0106667   0.08   0.4
```
