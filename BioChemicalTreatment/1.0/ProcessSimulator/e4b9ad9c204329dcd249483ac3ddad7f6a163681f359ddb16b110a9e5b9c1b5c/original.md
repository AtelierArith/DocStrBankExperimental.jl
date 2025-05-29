```
InflowPortToRealOutput(components; initial_flow=nothing, initial_concentrations=nothing, name)
```

A system which connects to a [`InflowPort`](@ref) and to a series of [`ModelingToolkitStandardLibrary.Blocks.RealOutput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) on the other sides for compatibility with the ModelingToolkitStandardLibrary. Internally the equations ensure equality inbetween the corresponding symbols. Takes the same inputs as [`InflowPort`](@ref).

!!! info
    This function needs the [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) to be loaded, as it is only useful with this library.


# Connectors

  * `inflow`: The [`InflowPort`](@ref) to connect
  * `q`: A [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref) for the flow rate
  * One [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref) for each component in the flow
