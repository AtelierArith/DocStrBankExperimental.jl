```
AbstractMultiChannelColor{T<:Number,N}
```

An abstract type for multichannel/multiband/hyperspectral colors. Concrete derived types should have a field, `channels`, which is a `NTuple{N,T}`. The channels can be returned with `Tuple(c::AbstractMultiChannelColor)`.
