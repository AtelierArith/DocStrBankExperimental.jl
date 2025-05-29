```
last_time = periodic_wait(P::AbstractProcess, last_time, dt)
```

Should continue execution at start of next period, i.e. when `dt` seconds has passed since `last_time`. 

For a `PhysicalProcess` this has a default implementation which sleeps until `last_time + dt` using  `Libc.systemsleep`. Though this is more precise than using the standard `sleep` in Julia, it also  blocks the entire Julia thread it is running on which could affect execution in some cases.

For a `SimulatedProcess` it can either be running in realtime in a background process, in which case  it should be implemented similarly to the physical process, or it runs at full simulation speed, in  which case the environment should simulate a step corresponding to `dt` time when `periodic_wait` is called.

A good way to initialize `last_time` to the correct value is to call `last_time = periodic_wait(P, 0.0, 0.0)`.
