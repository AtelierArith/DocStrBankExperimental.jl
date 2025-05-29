```
upwind_operators(periodic_derivative_operator;
                 derivative_order = 1, accuracy_order,
                 xmin, xmax, N,
                 mode = FastMode()))
```

Create [`PeriodicUpwindOperators`](@ref) from operators constructed by [`periodic_derivative_operator`](@ref). The keyword arguments are passed directly to [`periodic_derivative_operator`](@ref).

## Examples

```jldoctest
julia> D = upwind_operators(periodic_derivative_operator, accuracy_order = 2,
                            xmin = 0//1, xmax = 8//1, N = 8)
Upwind SBP first-derivative operators of order 2 on a grid in [0//1, 7//1] using 8 nodes
and coefficients of Fornberg1998

julia> D.minus
Periodic first-derivative operator of order 2 on a grid in [0//1, 8//1] using 8 nodes,
stencils with 2 nodes to the left, 0 nodes to the right, and coefficients of Fornberg (1998)
  Calculation of Weights in Finite Difference Formulas.
  SIAM Rev. 40.3, pp. 685-691.

julia> D.plus
Periodic first-derivative operator of order 2 on a grid in [0//1, 8//1] using 8 nodes,
stencils with 0 nodes to the left, 2 nodes to the right, and coefficients of Fornberg (1998)
  Calculation of Weights in Finite Difference Formulas.
  SIAM Rev. 40.3, pp. 685-691.
```

```julia
julia> Matrix(D.central)
8×8 Matrix{Rational{Int64}}:
  0//1   1//1  -1//4   0//1   0//1   0//1   1//4  -1//1
 -1//1   0//1   1//1  -1//4   0//1   0//1   0//1   1//4
  1//4  -1//1   0//1   1//1  -1//4   0//1   0//1   0//1
  0//1   1//4  -1//1   0//1   1//1  -1//4   0//1   0//1
  0//1   0//1   1//4  -1//1   0//1   1//1  -1//4   0//1
  0//1   0//1   0//1   1//4  -1//1   0//1   1//1  -1//4
 -1//4   0//1   0//1   0//1   1//4  -1//1   0//1   1//1
  1//1  -1//4   0//1   0//1   0//1   1//4  -1//1   0//1
```
