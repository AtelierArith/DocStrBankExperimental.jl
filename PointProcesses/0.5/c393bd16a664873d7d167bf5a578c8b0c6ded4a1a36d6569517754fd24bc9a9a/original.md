```
BoundedPointProcess{M,P,T} <: AbstractPointProcess{M}
```

Temporal point process `P` with pre-defined start and end times.

Implements some fallbacks for the `AbstractPointProcess` interface which accept fewer arguments.

# Fields

  * `pp::P`: underlying point process
  * `tmin::T`: start time
  * `tmax::T`: end time
