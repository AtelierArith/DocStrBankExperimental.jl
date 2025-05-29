```
fixed_timesteps!(control,Δt; grow=1.0)
```

Modify control data such that the time steps are fixed to a geometric sequence such that Δt*new=Δt*old*grow
