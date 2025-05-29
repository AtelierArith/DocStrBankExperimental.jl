```
RotatingTimeValue{R, T}
```

A wrapper around a time value for distinguishing potentially different rotation group it could belong to in a rotating sampling design. See also [`rotatingtime`](@ref) and [`settime`](@ref).

# Fields

  * `rotation::R`: a rotation group in a rotating sampling design.
  * `time::T`: a time value belonged to the rotation group.
