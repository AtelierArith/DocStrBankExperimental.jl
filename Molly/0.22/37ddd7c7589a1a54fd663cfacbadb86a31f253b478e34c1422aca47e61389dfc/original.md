```
System(crystal; <keyword arguments>)
```

Construct a `System` from a SimpleCrystals.jl `Crystal` struct.

Properties unused in the simulation or in analysis can be left with their default values. `atoms`, `atoms_data`, `coords` and `boundary` are automatically calculated from the `Crystal` struct. Extra atom paramaters like `σ` have to be added manually after construction using the convenience constructor `System(sys; <keyword arguments>)`.
