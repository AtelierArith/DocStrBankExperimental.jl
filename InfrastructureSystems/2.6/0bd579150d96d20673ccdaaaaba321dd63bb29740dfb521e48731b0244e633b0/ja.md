```julia
is_concave(
    pwl::InfrastructureSystems.PiecewiseLinearData
) -> Bool

```

基礎データの凹性に応じてTrue/Falseを返します。区分線形データの場合、傾きの列が非増加であるかどうかをチェックします。
