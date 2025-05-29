```julia
Probabilistic(
    src::InfrastructureSystems.Probabilistic,
    name::AbstractString;
    scaling_factor_multiplier
) -> InfrastructureSystems.Probabilistic

```

既存のインスタンスからデータを共有するProbabilisticを構築します。

これは、コンポーネントが2つの異なる属性に対して同じ時系列データを使用する必要がある場合に便利です。
