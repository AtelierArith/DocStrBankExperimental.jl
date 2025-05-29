```
interpolate_fn(
    f::Function,
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    points::T where {T<:Matrix};
    method::Symbol = :default,
)
```

Function that interpolates a function `f` over a set of variables (or affine expressions). The number of columns of the `points` matrix should be the same as the length of the `x_vector`. 

### Required arguments

`f` a possibly multidimensional function that takes a vector of arguments the same length as `x_vector`.

`x_vector` a vector of variables or expressions that are the input vector for `f`.

`points` is a `Matrix` that specifies the sample points for the function.

### Optional arguments

`method` if the formulation method and can be set to `:convex`, `:SOS1`, `:binary` or `:bisection`.
