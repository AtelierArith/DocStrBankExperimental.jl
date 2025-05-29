```
InfiniteTimeReward{R <: Real, AR <: AbstractArray{R}}
```

`InfiniteTimeReward`は、各状態に各反復で割り当てられる報酬の特性と、保証された収束のための割引率です。時間の地平線は無限であり、すなわち $H = \infty$ であるため、最適な方針は定常的になります。
