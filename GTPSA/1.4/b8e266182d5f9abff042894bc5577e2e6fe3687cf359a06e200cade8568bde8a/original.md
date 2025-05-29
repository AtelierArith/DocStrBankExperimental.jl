```
getord!(t::TPS{T}, t1::TPS{T}, order::Integer) where {T} -> t
```

Extracts one homogenous polynomial from `t1` of the given order and  sets `t` to the result in-place.
