```julia
mutable struct Interpolant{TMB, INB, ITP}
```

Constructs a linnear interpolant that interpolates between the poinsts `(tinit, coefinit)` and `(tfinal, coeffinal)`.

# Fields

  * `timebuf::Any`: Buffer to record time
  * `databuf::Any`: Buffer to record data
  * `itp::Any`: Internal interpolating function
