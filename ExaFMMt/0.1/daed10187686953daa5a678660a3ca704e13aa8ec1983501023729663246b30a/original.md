```
setup(
    sources::Matrix{F},
    targets::Matrix{F},
    fmmoptions::ModifiedHelmholtzFMMOptions{I, F}
) where {I, F <: Real}
```

Sets FMM structure up in the C++ part and allocates all madatory storage.

# Arguments

  * `sources::Matrix{F}`: 3d-coordinates of sources.
  * `targets::Matrix{F}`: 3d-coordinates of targets.
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, F}`: Julia modified-Helmholtz-initializer for setup function.
