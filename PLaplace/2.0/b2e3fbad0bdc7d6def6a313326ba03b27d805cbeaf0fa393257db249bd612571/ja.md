```julia
append!(
    A::PLaplace.ErrorData,
    B::PLaplace.ErrorData
) -> Vector{Vector{Float64}}

```

オブジェクトのタイプ [ErrorData](@ref) に対して、Bのすべての要素をAの要素に追加します。
