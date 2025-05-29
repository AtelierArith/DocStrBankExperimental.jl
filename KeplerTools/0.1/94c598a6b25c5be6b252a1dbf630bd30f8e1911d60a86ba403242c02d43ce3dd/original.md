```
t = true_to_time(θ, e, T, Mo=0, epoch=0, tmin=nothing)
```

Computes the time at which an orbit with eccentricity `e`, period `T`, mean anomaly at epoch `Mo`, and epoch `epoch` has the specified true anomaly `θ`.

Because this time is not uniquely defined for elliptical orbits, `tmin` can be specified to ensure that the returned time falls between `tmin` and `tmin + T`.
