```
antecedent(m::Union{Rule,Branch})::Formula
```

ルール/ブランチの前提を返します。つまり、モデルを適用する際にチェックされるべき式です。

関連情報としては、[`apply`](@ref)、[`consequent`](@ref)、[`checkantecedent`](@ref)、[`Rule`](@ref)、[`Branch`](@ref)があります。
