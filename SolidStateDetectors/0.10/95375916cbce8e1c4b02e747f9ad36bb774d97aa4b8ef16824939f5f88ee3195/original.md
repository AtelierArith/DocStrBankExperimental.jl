```
ssd_read(filename::AbstractString, ::Type{Simulation})
```

Reads a [`Simulation`](@ref) from a HDF5 file with a given `filename`  using [LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl).

## Arguments

  * `filename::AbstractString`: Filename of the HDF5 file.

## Example

```julia
using SolidStateDetectors
using LegendHDF5IO
sim = ssd_read("example_sim.h5", Simulation)
```

See also [`ssd_write`](@ref).
