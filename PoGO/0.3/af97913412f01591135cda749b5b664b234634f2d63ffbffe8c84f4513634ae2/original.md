```
plot_approximation(
    optimizer,
    func::Function,
    lb::Real,
    ub::Real,
    δ::Real,
    type::Symbol;
    detail::Int = 3,
    knots::Union{Nothing,Vector{Float64},Vector{Tuple{Float64,Symbol}}} = nothing,
)
```

Function that returns a set of points corresponding to an approximation of the function `func`.
