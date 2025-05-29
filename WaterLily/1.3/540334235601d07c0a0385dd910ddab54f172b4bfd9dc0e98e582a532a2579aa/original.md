```
sim_step!(sim::Simulation,t_end=sim(time)+Δt;max_steps=typemax(Int),remeasure=true,verbose=false)
```

Integrate the simulation `sim` up to dimensionless time `t_end`. If `remeasure=true`, the body is remeasured at every time step. Can be set to `false` for static geometries to speed up simulation.
