```
RunResult(
    success::Bool,
    error_weight::Int,
    logical_commutations::Union{Nothing,BitVector}
    custom_values::Union{Nothing,Vector}
)
```

[`qec_run_once`](@ref) によって返される実行結果を構築します。

# 例

```jldoctest
julia> r = RunResult(false, 2, BitVector([0, 1]), [1.2, 3.1])
RunResult{Vector{Float64}}(false, 2, Bool[0, 1], [1.2, 3.1])

julia> r.success, r.error_weight, r.logical_commutations, r.custom_values
(false, 2, Bool[0, 1], [1.2, 3.1])
```
