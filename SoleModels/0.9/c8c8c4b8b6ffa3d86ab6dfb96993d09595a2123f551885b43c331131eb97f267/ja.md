```
antecedent(m::Union{Rule,Branch})::Formula
```

[`Rule`](@ref) または [`Branch`](@ref) の前提を返します。つまり、モデルを適用する際にチェックされる式です。

他にも [`apply`](@ref)、[`Branch`](@ref)、[`checkantecedent`](@ref)、[`consequent`](@ref)、[`Rule`](@ref) を参照してください。
