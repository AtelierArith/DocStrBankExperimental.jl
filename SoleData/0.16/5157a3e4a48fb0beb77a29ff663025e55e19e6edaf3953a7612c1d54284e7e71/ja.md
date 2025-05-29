```
struct MultiFormula{F<:Formula} <: AbstractSyntaxStructure
    modforms::Dict{Int,F}
end
```

異なるモダリティ間の式の論理積を表す `MultiLogiset` でチェックできる論理式。

関連項目として [`MultiLogiset`](@ref)、[`eachmodality`](@ref)、[`nmodalities`](@ref)、[`modforms`](@ref) を参照してください。
