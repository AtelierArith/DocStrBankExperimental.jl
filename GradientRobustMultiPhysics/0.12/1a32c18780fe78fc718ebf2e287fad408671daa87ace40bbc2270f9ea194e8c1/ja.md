```julia
DiscreteLumpedBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{LumpedBilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteLumpedBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{LumpedBilinearForm, Float64, ON_CELLS}

```

(離散) ランプド双線形形式アセンブリパターンを作成します。詳細については、双線形形式コンストラクタを参照してください。
