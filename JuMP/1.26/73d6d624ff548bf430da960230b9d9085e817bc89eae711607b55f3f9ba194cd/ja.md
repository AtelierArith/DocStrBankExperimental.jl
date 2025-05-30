```
nonlinear_model(
    model::GenericModel;
    force::Bool = false,
)::Union{MOI.Nonlinear.Model,Nothing}
```

もし `model` に非線形コンポーネントがある場合は、[`MOI.Nonlinear.Model`](@ref) を返し、そうでなければ `nothing` を返します。

`force` が `true` の場合は、常に [`MOI.Nonlinear.Model`](@ref) を返し、モデルに存在しない場合は空のものを作成します。

!!! compat
    この関数はレガシー非線形インターフェースの一部です。 [非線形モデリング](@ref) に記載されている新しい非線形インターフェースの使用を検討してください。

