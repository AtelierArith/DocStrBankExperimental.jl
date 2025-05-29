```
getRingPixels(map::HealpixMap{T,RingOrder,AA}, ring_info::RingInfo) where {T <: Real, AA <: AbstractArray{T,1}}
getRingPixels(map::HealpixMap{T,RingOrder,AA}, ring_idx::Integer) where {T <: Real, AA <: AbstractArray{T,1}}
```

指定された `ring_info` または `ring_idx` に対応する `map` 内のピクセルのスライス（`view`）を参照で返します。
