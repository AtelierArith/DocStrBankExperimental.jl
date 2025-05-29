```
model_accumulation!(acc, sim::HelperSimulator, x, dt = 1.0;
    forces = setup_forces(sim.model),
    update_secondary = true,
    kwarg...
)
```

Compute the accumulation term into Vector acc.
