```
StopWhenCovarianceIllConditioned <: StoppingCriterion
```

条件数が共分散行列の閾値を超えた場合、CMA-ESを停止します。これは[Hansen:2023](@cite)の`ConditionCov`条件に対応します。
