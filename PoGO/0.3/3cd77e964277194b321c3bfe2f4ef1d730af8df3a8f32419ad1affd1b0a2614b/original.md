```
interpolate_points(
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::T where {T<:Matrix};
    method::Symbol = :default,
)
```

Function that interpolates over a set of variables (or affine expressions). The number of columns of the `points` matrix should be greater than or equal to the length of the `x_vector`. For any extra columns, new variables will be defined, and their values will be interpolated. 

### Required arguments

`x_vector` a vector of variables or expressions around which the triangulation will be formed.

`points` is a `Matrix` that specifies the points to be interpolated.

### Optional arguments

`method` if the formulation method and can be set to `:convex`, `:SOS1`, `:binary` or `:bisection`.
