```
RealInputToOutflowPort(components; initial_flow=nothing, initial_concentrations=nothing, name)
```

A system which connects to a [`OutflowPort`](@ref) and to a series of [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) on the other sides for compatibility with the ModelingToolkitStandardLibrary. The system ensures equality between the corresponding symbols.  Takes the same inputs as [`OutflowPort`](@ref).

!!! info
    This function needs the [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) to be loaded, as it is only useful with this library.


# Connectors

  * `outflow`: The [`OutflowPort`](@ref) to connect
  * `q`: A [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) for the flow rate
  * One [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) for each component in the flow
