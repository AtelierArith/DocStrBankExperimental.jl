```julia
tryfix(
    a::Union{Array{T, 2}, ExtendableGrids.VariableTargetAdjacency{T}}
) -> Any

```

可変ターゲット隣接を固定ターゲット隣接に変換しようとします。
