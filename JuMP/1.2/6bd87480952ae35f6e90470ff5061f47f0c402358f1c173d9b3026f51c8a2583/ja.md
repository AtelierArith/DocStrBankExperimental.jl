```
nonlinear_model(
    model::Model;
    force::Bool = false,
)::Union{MOI.Nonlinear.Model,Nothing}
```

`model`に非線形コンポーネントがある場合は、[`MOI.Nonlinear.Model`](@ref)を返し、そうでなければ`nothing`を返します。

`force`が`true`の場合は、常に[`MOI.Nonlinear.Model`](@ref)を返し、モデルに存在しない場合は空のものを作成します。
