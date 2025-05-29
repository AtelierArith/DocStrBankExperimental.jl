```
const Operator = Union{Connective,Truth}
```

任意のアリティの論理定数のためのユニオン型（`Truth` 値の場合はゼロ、`Connective` の場合は非ゼロ）。

関連情報として [`Connective`](@ref)、[`Truth`](@ref) を参照してください。
