```
RunResult(
    success::Bool,
    error_weight::Int,
    logical_commutations::Union{Nothing,BitVector}
    custom_values::Union{Nothing,Vector}
)
```

Construct a run result as returned by [`qec_run_once`](@ref).

# Examples

```jldoctest
julia> r = RunResult(false, 2, BitVector([0, 1]), [1.2, 3.1])
RunResult{Vector{Float64}}(false, 2, Bool[0, 1], [1.2, 3.1])

julia> r.success, r.error_weight, r.logical_commutations, r.custom_values
(false, 2, Bool[0, 1], [1.2, 3.1])
```
