```
RealInputToReactionOutput(components; initial_rates=nothing, name)
```

A system which connects to a [`ReactionOutputPort`](@ref) and to a series of [`ModelingToolkitStandardLibrary.Blocks.RealInput`s](@extref ModelingToolkitStandardLibrary.Blocks.RealInput) on the other sides for compatibility with the ModelingToolkitStandardLibrary. The system ensures equality between the corresponding symbols.  Takes the same inputs as [`ReactionOutputPort`](@ref).

!!! info
    This function needs the [`ModelingToolkitStandardLibrary`](@extref ModelingToolkitStandardLibrary :doc:`index`) to be loaded, as it is only useful with this library.


# Connectors

  * `reactionoutput`: The [`ReactionOutputPort`](@ref) to connect
  * One [`ModelingToolkitStandardLibrary.Blocks.RealInput`](@extref) for each component
