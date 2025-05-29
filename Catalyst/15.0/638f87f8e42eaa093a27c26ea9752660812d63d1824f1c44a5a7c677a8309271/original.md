```
species(network)
```

Given a [`ReactionSystem`](@ref), return a vector of all species defined in the system and any subsystems that are of type `ReactionSystem`. To get the species and non-species variables in the system and all subsystems, including non-`ReactionSystem` subsystems, uses `unknowns(network)`.

Notes:

  * If `ModelingToolkit.get_systems(network)` is non-empty will allocate.
