```
function objective_itd_min_fuel_polynomial_distribution_load_setpoint_delta_simple(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractPowerModel,
    pmd::_PMD.AbstractUnbalancedPowerModel
)
```

分配のための伝送および負荷セットポイントデルタ（連続負荷削減）の多項式項における燃料コスト最小化目的。
