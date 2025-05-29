```
upwind_operators(source_type, args...; derivative_order = 1, kwargs...)
```

Create [`UpwindOperators`](@ref) from the given source type. The positional arguments `args...` and keyword arguments `kwargs...` are passed directly to [`derivative_operator`](@ref).

## Examples

```jldoctest
julia> D = upwind_operators(Mattsson2017, accuracy_order = 2,
                            xmin = 0//1, xmax = 9//1, N = 10)
Upwind SBP first-derivative operators of order 2 on a grid in [0//1, 9//1] using 10 nodes
and coefficients of Mattsson2017

julia> D.minus
SBP first-derivative operator of order 2 on a grid in [0//1, 9//1] using 10 nodes
and coefficients of Mattsson (2017)
  Diagonal-norm upwind SBP operators.
  Journal of Computational Physics 335, pp. 283-310.
  (upwind coefficients minus)

julia> D.plus
SBP first-derivative operator of order 2 on a grid in [0//1, 9//1] using 10 nodes
and coefficients of Mattsson (2017)
  Diagonal-norm upwind SBP operators.
  Journal of Computational Physics 335, pp. 283-310.
  (upwind coefficients plus)
```

```julia
julia> Matrix(D.central)
10×10 Matrix{Rational{Int64}}:
 -2//1   3//1  -1//1   0//1   0//1   0//1   0//1   0//1   0//1   0//1
 -3//5   0//1   4//5  -1//5   0//1   0//1   0//1   0//1   0//1   0//1
  1//4  -1//1   0//1   1//1  -1//4   0//1   0//1   0//1   0//1   0//1
  0//1   1//4  -1//1   0//1   1//1  -1//4   0//1   0//1   0//1   0//1
  0//1   0//1   1//4  -1//1   0//1   1//1  -1//4   0//1   0//1   0//1
  0//1   0//1   0//1   1//4  -1//1   0//1   1//1  -1//4   0//1   0//1
  0//1   0//1   0//1   0//1   1//4  -1//1   0//1   1//1  -1//4   0//1
  0//1   0//1   0//1   0//1   0//1   1//4  -1//1   0//1   1//1  -1//4
  0//1   0//1   0//1   0//1   0//1   0//1   1//5  -4//5   0//1   3//5
  0//1   0//1   0//1   0//1   0//1   0//1   0//1   1//1  -3//1   2//1
```
