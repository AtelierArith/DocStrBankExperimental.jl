```
reset_maps!(d::DestripingData{T, O}) where {T <: Real, O <: Healpix.Order}
```

Set the skymap and the hitmap in `d` to zero. Nothing is done on the other fields.
