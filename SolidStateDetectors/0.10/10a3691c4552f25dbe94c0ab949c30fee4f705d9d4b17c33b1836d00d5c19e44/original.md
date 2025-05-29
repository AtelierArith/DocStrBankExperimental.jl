```
ssd_write(filename::AbstractString, sim::Simulation)
```

Converts a [`Simulation`](@ref) to a `NamedTuple` and writes it to a HDF5 file  with a given `filename` using [LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl).

## Arguments

  * `filename::AbstractString`: Filename of the HDF5 file.
  * `sim::Simulation`: [`Simulation`](@ref) that should be written to the HDF5 file.

## Example

```julia
using SolidStateDetectors
using LegendHDF5IO
sim = Simulation(SSD_examples[:InvertedCoax])
simulate!(sim)
ssd_write("example_sim.h5", sim)
```

!!! warn
    If a file with `filename` already exists, it will be overwritten by this method.


See also [`ssd_read`](@ref).
