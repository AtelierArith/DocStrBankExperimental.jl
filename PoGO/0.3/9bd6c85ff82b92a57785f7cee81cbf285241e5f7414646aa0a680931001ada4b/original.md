```
interpolate_fn(
    f::Function,
    x_vector::Vector{<:Union{VariableRef,AffExpr}},
    grid::Vector{<:Union{AbstractRange,Vector{<:Real}}};
    method::Symbol = :default,
)
```

Function that interpolates a function `f` over a set of variables (or affine expressions). The `grid` vector should be the same length as the `x_vector`. 

### Required arguments

`f` a possibly multidimensional function that takes a vector of arguments the same length as `x_vector`.

`x_vector` a vector of variables or expressions that are the input vector for `f`.

`grid` is a vector of ranges or vectors that specify the sample points (which are the Cartesian product of the vectors) for the function `f`.

### Optional arguments

`method` if the formulation method and can be set to `:convex`, `:SOS1`, `:binary` or `:bisection`.
