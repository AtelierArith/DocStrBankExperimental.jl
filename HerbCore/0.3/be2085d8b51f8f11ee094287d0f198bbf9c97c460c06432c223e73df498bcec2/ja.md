```
AbstractHole <: AbstractRuleNode
```

[`AbstractHole`](@ref) は、文法の特定のルールがまだ適用できるプレースホルダーです。[`AbstractHole`](@ref) の `domain` は、どのルールが適用できるかを定義します。`domain` はビットベクターであり、`i` 番目のビットが真に設定されている場合、文法の `i` 番目のルールが適用できることを示します。
