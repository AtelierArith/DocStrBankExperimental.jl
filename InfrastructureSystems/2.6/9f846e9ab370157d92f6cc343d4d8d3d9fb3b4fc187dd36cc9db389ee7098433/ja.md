```julia
Scenarios(
    src::InfrastructureSystems.Scenarios,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.Scenarios

```

既存のインスタンスからデータを共有するScenariosを構築します。

これは、コンポーネントが2つの異なる属性に対して同じ時系列データを使用したい場合に便利です。
