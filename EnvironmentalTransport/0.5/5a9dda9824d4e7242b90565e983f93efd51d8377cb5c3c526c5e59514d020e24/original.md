```julia
Puff(
    di::EarthSciMLBase.DomainInfo;
    name
) -> ModelingToolkit.ODESystem

```

Create a Lagrangian transport model which advects a "puff" or particle of matter within a fluid velocity field.

Model boundaries are set by the DomainInfo argument. The model sets boundaries at the ground and model bottom and top, preventing the puff from crossing those boundaries. If the puff reaches one of the horizontal boundaries, the simulation is stopped.
