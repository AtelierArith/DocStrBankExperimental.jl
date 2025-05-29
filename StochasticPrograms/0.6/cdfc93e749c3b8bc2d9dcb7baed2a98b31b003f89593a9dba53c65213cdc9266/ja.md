```
@known(def)
```

前の段階で行われた各決定を注釈します。[`@stochastic_model`](@ref) 定義に含まれる任意の [`@decision`](@ref) は、以降の段階に `@known` 注釈を暗黙的に追加します。

## 例

```julia
@known x₁, x₂
```

他にも [`@decision`](@ref)、[`@parameters`](@ref)、[`@uncertain`](@ref)、[`@stage`](@ref) を参照してください。
