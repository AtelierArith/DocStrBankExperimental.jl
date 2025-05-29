```
discretize(ahs::AnalogHamiltonianSimulation, device::Device)
```

Creates a new [`AnalogHamiltonianSimulation`](@ref) with all numerical values represented as `Dec128` objects with fixed precision based on the capabilities of the `device`.
