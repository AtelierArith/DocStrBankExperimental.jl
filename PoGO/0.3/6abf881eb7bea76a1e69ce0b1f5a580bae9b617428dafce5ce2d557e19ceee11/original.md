```
approximate(
    x::Union{VariableRef,AffExpr},
    func::Function,
    n::Int = 0;
    δ::Real = 0.0,
    method::Symbol = :default,
    type::Symbol = :interior,
    knots::Union{Nothing,Vector{Float64},Vector{Tuple{Float64,Symbol}}} = nothing,
    name::String = "",
)
```

Function that defines a mixed-integer programming formulation for an arbitrary univariate function.

### Required arguments

`x` is either of type `VariableRef` or `AffExpr` and is the input variable for the function `func`.

`func` is the function that we are approximating.

### Optional arguments

`n` the number of points sampled between knots (ignored if `δ` is used).

`δ` is the minimum distance between sample points.

`method` is the method of the approximation. This can be set to `:binary`, `:echelon`, `:convex`, `:bisection`, `:SOS1` or `:SOS2`.

`type` specifies how the approximation bounds the actual function. This can be set to `:upper`, `:lower`, `:interior`, `tangent_cuts` or `:combined`.

`knots` must list the function's discontinuities, and points of inflection. Can be provided with curvature specifed, but if not this will be determined automatically.

`name` can be set to give the variables created meaningful names.
