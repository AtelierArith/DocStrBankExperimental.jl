```
CollisionModel()
```

Type to be used as `plr_func` when instantiating [`PLR_SimulationParameters`](@ref) or [`PLR_Simulation`](@ref), which will mimic a collision model for the PHY abstraction.

!!! note
    An instance of `CollisionModel` is not callable like all other `plr_func` values, the collision model is just implemented directly inside the inner code performing the simulation.

