```
compress_timesteps(timesteps, forces = nothing; max_step = Inf)
```

Compress a set of timesteps and forces to the largest possible steps that still covers the same interval and changes forces at exactly the same points in time, while being limited to a maximum size of `max_step`.
