```julia
parameter_bounds(
    _::ContinuumMechanicsBase.AbstractMaterialModel,
    _::ContinuumMechanicsBase.AbstractMaterialTest
) -> @NamedTuple{lb::Nothing, ub::Nothing}

```

最適化のためのタプル内の各パラメータのデフォルト境界。特定のモデルに対するメソッドディスパッチなしで、定数は範囲[-∞, ∞]で「最適化」される可能性があります。これが現実的かどうかは判断してください。
