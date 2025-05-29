```
applyFullWeights!(m::PolarizedHealpixMap{T, RingOrder}, [wgt::Vector{T}]) where T
```

偏光マップにピクセル重み付けを適用して、より正確なSHTを得ます。

# 引数:

  * `m::PolarizedHealpixMap{T, RingOrder}`: 修正するマップ
  * `wgt::Vector{T}` (オプション): 圧縮されたピクセル重み。指定されていない場合、アーティファクトが探されます。
