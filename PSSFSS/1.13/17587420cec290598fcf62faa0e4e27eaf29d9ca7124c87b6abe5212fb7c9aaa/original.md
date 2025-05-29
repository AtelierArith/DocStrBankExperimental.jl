```
Package PSSFSS v1.13.1
```

`PSSFSS` is a software package for the analysis of planar polarization and frequency selective surfaces (PSSs and FSSs). The user specifies the geometry to be analyzed as a `Vector` containing two or more dielectric [`Layer`](@ref)s  and zero or more [`Sheet`](@ref) objects denoting the PSS/FSS surfaces.  After also specifying the scan angles or unit cell incremental phasings, frequencies to be considered,   the user then invokes the [`analyze`](@refs) function to perform the analysis. Performance parameters such as  axial ratio, insertion loss, return loss, reflection phase, etc. are easily retrieved using the  [`extract_result`](@ref) function in combination with the [`@outputs`](@ref) macro. FSS/PSS sheet triangulations can be conveniently visualized using the `plot` command of the `Plots` package.

Extensive documentation is available at https://simonp0420.github.io/PSSFSS.jl/
