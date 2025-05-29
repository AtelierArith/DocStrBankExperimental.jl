```
simulate_component(rng, c::AbstractComponent, simulation::Simulation)
```

By default call `simulate_component` with `(rng, c::Abstractcomponent, design::AbstractDesign)` instead of the whole simulation. This function exist solely to provide a "hook" if for a custom component something else than the design is necessary, e.g. a dependency on the onsets, noise or similar.
