```
getRingPixels(map::HealpixMap{T,RingOrder,AA}, ring_info::RingInfo) where {T <: Real, AA <: AbstractArray{T,1}}
getRingPixels(map::HealpixMap{T,RingOrder,AA}, ring_idx::Integer) where {T <: Real, AA <: AbstractArray{T,1}}
```

Returns by reference a slice (`view`) of the pixels in `map` corresponding to the given `ring_info` or `ring_idx`.
