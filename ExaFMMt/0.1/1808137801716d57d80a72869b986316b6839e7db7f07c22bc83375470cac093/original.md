```
setup(
    sources::Matrix{F},
    targets::Matrix{F},
    fmmoptions::HelmholtzFMMOptions{I, C}
) where {I, F <: Real, C <: Complex}
```

Sets FMM structure up in the C++ part and allocates all madatory storage.

# Arguments

  * `sources::Matrix{F}`: 3d-coordinates of sources.
  * `targets::Matrix{F}`: 3d-coordinates of targets.
  * `fmmoptions::HelmholtzFMMOptions{I, C}`: Julia Helmoltz-initializer for setup function.
