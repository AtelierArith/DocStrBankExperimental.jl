```
mask!(m::HealpixMap, mask)
mask!(m::PolarizedHealpixMap, maskT, maskP)
```

マップまたは偏光マップをその場でマスクします。

# 引数:

  * `m::Union{HealpixMap,PolarizedHealpixMap}`: マスクするマップまたは偏光マップ
  * `maskT::HealpixMap`: 最初のマップの強度用マスク
  * `maskP::HealpixMap`: 最初のマップの偏光用マスク
