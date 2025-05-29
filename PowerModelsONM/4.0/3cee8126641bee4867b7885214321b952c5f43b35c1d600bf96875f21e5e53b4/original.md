```
constraint_energized_blocks_strictly_increasing(pm::AbstractUnbalancedPowerModel, n_1::Int, n_2::Int)
```

Constraint to ensure that the number of energized load blocks from one timestep to another is strictly increasing and that once energized, a load block cannot be shed in a later timestep.
