```
setup(
    sources::Matrix{F},
    targets::Matrix{F}, 
    fmmoptions::LaplaceFMMOptions{I}
) where {I, F <: Real}
```

Sets FMM structure up in the C++ part and allocates all madatory storage.

# Arguments

  * `sources::Matrix{F}`: 3d-coordinates of sources.
  * `targets::Matrix{F}`: 3d-coordinates of targets.
  * `fmmoptions::LaplaceFMMOptions{I}`: Julia Laplace-initializer for setup function.
