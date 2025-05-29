```
TimeSeries{T <: Number} <: MonteCarloMeasurement
```

A type of [`MonteCarloMeasurement`](@ref) that stores the measurements in a  `datastream::Vector{T}`. Statistics are not accumulated in an *online* way.
