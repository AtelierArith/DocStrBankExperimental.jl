```
StateInputToRealOutput(components; initial_rates=nothing, name)
```

A system which connects to a [`StateInputPort`](@ref) and to a series of [`ModelingToolkitStandardLibrary.Blocks.RealOutput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealOutput) on the other sides for compatibility with the ModelingToolkitStandardLibrary. The system ensures equality between the corresponding symbols.  Takes the same inputs as [`StateInputPort`](@ref).

!!! info
    This function needs the [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) to be loaded, as it is only useful with this library.


# Connectors

  * `stateinput`: The [`StateInputPort`](@ref) to connect
  * One [`ModelingToolkitStandardLibrary.Blocks.RealOutput`](@extref) for each component
