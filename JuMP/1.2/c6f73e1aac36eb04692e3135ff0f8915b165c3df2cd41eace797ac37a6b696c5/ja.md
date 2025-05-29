```
optimizer_with_attributes(optimizer_constructor, attrs::Pair...)
```

最適化子コンストラクタを属性のリスト `attrs` とグループ化します。これは `MOI.OptimizerWithAttributes` と同等であることに注意してください。

`Model` コンストラクタまたは [`set_optimizer`](@ref) に提供されると、`optimizer_constructor()` を呼び出して最適化子を作成し、その後 [`set_optimizer_attribute`](@ref) を使用して属性を設定します。

## 例

```julia
model = Model(
    optimizer_with_attributes(
        Gurobi.Optimizer, "Presolve" => 0, "OutputFlag" => 1
    )
)
```

は次のように等価です：

```julia
model = Model(Gurobi.Optimizer)
set_optimizer_attribute(model, "Presolve", 0)
set_optimizer_attribute(model, "OutputFlag", 1)
```

## 注意

属性の文字列名は各ソルバーに特有です。興味のある属性を見つけるために、ソルバーのドキュメントを参照する必要があります。

関連情報: [`set_optimizer_attribute`](@ref), [`set_optimizer_attributes`](@ref), [`get_optimizer_attribute`](@ref).
