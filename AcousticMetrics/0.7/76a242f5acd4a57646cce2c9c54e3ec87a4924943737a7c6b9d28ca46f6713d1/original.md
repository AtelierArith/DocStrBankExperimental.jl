```
ApproximateOctaveBands{LCU,TF} <: AbstractProportionalBands{1,LCU,TF}
```

Representation of the approximate octave proportional frequency bands with `eltype` `TF`.

The `LCU` parameter can take one of three values:

  * `:lower`: The `struct` returns the lower edges of each frequency band.
  * `:center`: The `struct` returns the center of each frequency band.
  * `:upper`: The `struct` returns the upper edges of each frequency band.
