```julia
differentiate_solution(
    ,
    primal_vals::Vector{Float64},
    eq_dual_vals::Vector{Float64},
    ineq_dual_vals::Vector{Float64},
    parameter_values::Dict{Symbol, Float64};
    scale
) -> Any

```

Differentiate a solution of a model. The first argument is the output of [`differentiate_prepare_kkt`](@ref), and is a tuple of the deconstructed model. The following arguments (`primal_vals`, `eq_dual_vals`, `ineq_dual_vals`) are outputs of [`optimized_values`](@ref). `parameter_values`
