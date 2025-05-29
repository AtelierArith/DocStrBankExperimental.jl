```
RealInputToStateOutput(components; initial_state=nothing, name)
```

A system which connects to a [`StateOutputPort`](@ref) and to a series of [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) on the other sides for compatibility with the ModelingToolkitStandardLibrary. The system ensures equality between the corresponding symbols.  Takes the same inputs as [`StateOutputPort`](@ref).

!!! info
    This function needs the [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) to be loaded, as it is only useful with this library.


# Connectors

  * `stateoutput`: The [`StateOutputPort`](@ref) to connect
  * One [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) for each state
