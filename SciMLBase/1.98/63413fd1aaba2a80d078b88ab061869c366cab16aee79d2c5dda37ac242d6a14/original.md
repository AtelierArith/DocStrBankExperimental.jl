```
set_proposed_dt(i::DEIntegrator,dt)
set_proposed_dt(i::DEIntegrator,i2::DEIntegrator)
```

Sets the proposed `dt` for the next timestep. If the second argument isa `DEIntegrator`, then it sets the timestepping of the first argument to match that of the second one. Note that due to PI control and step acceleration, this is more than matching the factors in most cases.
