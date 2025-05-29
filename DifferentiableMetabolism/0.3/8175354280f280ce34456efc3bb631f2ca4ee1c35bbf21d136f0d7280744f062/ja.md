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

モデルの解を微分します。最初の引数は[`differentiate_prepare_kkt`](@ref)の出力であり、分解されたモデルのタプルです。次の引数（`primal_vals`、`eq_dual_vals`、`ineq_dual_vals`）は[`optimized_values`](@ref)の出力です。`parameter_values`
