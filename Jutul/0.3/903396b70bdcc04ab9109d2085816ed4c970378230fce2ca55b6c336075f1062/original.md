```
model_residual!(r, sim, x, x0 = missing, dt = 1.0;
    forces = setup_forces(sim.model),
    include_accumulation = true,
    kwarg...
)
```

Fill in the model residual into Vector r.
