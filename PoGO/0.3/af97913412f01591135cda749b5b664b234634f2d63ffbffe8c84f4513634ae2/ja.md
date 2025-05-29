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

関数 `func` の近似に対応する点のセットを返す関数です。
