```julia
DiscreteSymmetricBilinearForm(
    operators,
    FES;
    ...
) -> GradientRobustMultiPhysics.AssemblyPattern{SymmetricBilinearForm, Float64, ON_CELLS, _A, _B, GradientRobustMultiPhysics.NoAction} where {_A<:Real, _B<:Integer}
DiscreteSymmetricBilinearForm(
    operators,
    FES,
    action;
    T,
    AT,
    name,
    regions,
    apply_action_to
) -> GradientRobustMultiPhysics.AssemblyPattern{SymmetricBilinearForm, Float64, ON_CELLS}

```

(離散)対称双線形形式のアセンブリパターンを作成します。詳細については、BilinearFormコンストラクタを参照してください。
