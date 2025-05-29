```
function objective_itd_min_fuel_pwl_distribution_load_setpoint_delta_simple(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractPowerModel,
    pmd::_PMD.AbstractUnbalancedPowerModel
)
```

配電における伝送および負荷セットポイントデルタ（連続的な負荷削減）のピースワイズ線形項を含む燃料コスト最小化目的。
