```julia
mutable struct EqualityConstraint{T, N, Nc, Cs} <: ConstrainedDynamics.AbstractConstraint{T, N}
```

`EqualityConstraint`は[`Mechanism`](@ref)のコンポーネントであり、2つ以上の[`Body`](@ref)間の運動学的関係を記述するために使用されます。通常、`EqualityConstraint`は直接作成すべきではありません。代わりにジョイントプロトタイプを使用してください。例えば：

```julia
EqualityConstraint(Revolute(body1, body2, rotation_axis)).
```

# 重要な属性

  * `id`:       制約の一意のID。`Mechanism`に追加されたときに割り当てられます。
  * `name`:     制約の名前。名前はURDFから取得されるか、ユーザーによって割り当てられます。
  * `parentid`: 親ボディのID。
  * `childids`: 子ボディのID。
