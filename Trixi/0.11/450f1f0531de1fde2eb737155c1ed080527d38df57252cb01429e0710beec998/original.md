```
AveragingCallback(semi::SemidiscretizationHyperbolic, tspan; output_directory="out",
                  filename="averaging.h5")
```

!!! warning "Experimental code"
    This callback is experimental and may change in any future release.


A callback that averages the flow field described by `semi` which must be a semidiscretization of the compressible Euler equations in two dimensions. The callback records the mean velocity, mean speed of sound, mean density, and mean vorticity for each node over the time interval given by `tspan` and stores the results in an HDF5 file `filename` in the directory `output_directory`. Note that this callback does not support adaptive mesh refinement ([`AMRCallback`](@ref)).
