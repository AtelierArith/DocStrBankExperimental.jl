```
generate(
    error_model::SimpleErrorModel, code, p::Real, [rng::AbstractRNG=GLOBAL_RNG]
) -> BitVector
```

[`Model.probability_distribution`](@ref)に基づいて新しいIIDエラーを生成します。詳細は[`Model.generate`](@ref)を参照してください。

!!! note
    [`SimpleErrorModel`](@ref)の具体的なサブタイプに対しては、メソッド[`Model.probability_distribution`](@ref)を実装する必要があります。

