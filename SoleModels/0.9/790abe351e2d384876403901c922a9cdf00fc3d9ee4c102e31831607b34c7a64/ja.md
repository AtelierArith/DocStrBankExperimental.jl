```
checkantecedent(
    m::Union{Rule,Branch},
    args...;
    kwargs...
)
    check(antecedent(m), args...; kwargs...)
end
```

[`Rule`](@ref) または [`Branch`](@ref) のインスタンスまたはデータセットに対する [`antecedent`](@ref) をチェックします。

他にも [`antecedent`](@ref)、[`Rule`](@ref)、[`Branch`](@ref) を参照してください。
