```
bsplines!(dest, basis, x[, derivative]; kwargs...)
```

Calculate the values and/or derivatives of all non-zero B-splines of `basis` at `x` in-place (i.e., in `dest`).

If all B-splines of `basis` are zero at `x`, `nothing` is returned. If any B-splines are non-zero at `x`, an `OffsetArray` that wraps `dest` is returned. Its size and contents depend on the optional `derivative` argument:

  * If `derivative` is not given, the returned `OffsetArray` contains the value of the `i`-th B-spline at the index `i`. In this case, `dest` must be a vector of length `order(basis)`.
  * If `derivative == Derivative(N)`, the returned `OffsetArray` contains the `N`-th derivative of the `i`-th B-spline at the index `i`. Again, `dest` must be a vector of length `order(basis)`.
  * If `derivative == AllDerivatives(N)`, the returned `OffsetArray` contains the `m`-th derivative (`0 ≤ m < N`) of the `i`-th B-spline at the index `i, m`. In this case, `dest` must be a matrix of size `(order(basis), N)`.

Two optional keyword arguments can be used to increase performance:

  * `derivspace`: When calculating derivatives, some coefficients are stored in a matrix of size `(order(basis), order(basis))`. By default, the function allocates a new matrix. To avoid this, a pre-allocated matrix can be supplied with the `derivspace` keyword. It can only be used when calculating derivatives, i.e., with `Derivative(N)` where `N ≥ 1` or `AllDerivatives(N)` where `N ≥ 2`.
  * `leftknot`: If the index of the relevant interval (i.e., `intervalindex(basis(spline), x)`) is already known, it can be supplied with the `leftknot` keyword.

# Examples

```jldoctest
julia> basis = BSplineBasis(4, 0:5);

julia> dest = zeros(4);

julia> bsplines!(dest, basis, 2.4)
4-element OffsetArray(::Vector{Float64}, 3:6) with eltype Float64 with indices 3:6:
 0.03600000000000002
 0.5386666666666667
 0.41466666666666663
 0.01066666666666666

julia> parent(ans) === dest
true

julia> bsplines!(dest, basis, -1.0) # returns nothing

julia> dest = zeros(4, 3);

julia> bsplines!(dest, basis, 3.75, AllDerivatives(3))
4×3 OffsetArray(::Matrix{Float64}, 4:7, 0:2) with eltype Float64 with indices 4:7×0:2:
 0.00260417  -0.03125    0.25
 0.315104    -0.65625    0.25
 0.576823     0.265625  -1.625
 0.105469     0.421875   1.125

julia> parent(ans) === dest
true
```
