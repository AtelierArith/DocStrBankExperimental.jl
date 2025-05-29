```
readsnap(snapgroup, sim::Simulation; [warn = IOWARN[]]) → particles, time, step, next_id, rng[,...]
```

Loads the snapshot from `snapgroup`, using additional information from `sim`. Returns a tuple of state information that can be applied to the simulation using [`setstate`]((@ref)
