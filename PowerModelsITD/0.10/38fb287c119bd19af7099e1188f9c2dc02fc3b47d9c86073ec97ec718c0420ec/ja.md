```
function objective_itd_min_fuel_pwl_distribution_load_setpoint_delta(
    pmitd::AbstractPowerModelITD,
    pm::_PM.AbstractPowerModel,
    pmd::_PMD.AbstractUnbalancedPowerModel
)
```

配電における伝送および負荷セットポイントのデルタにおける区分線形項を用いた燃料コスト最小化目的。
