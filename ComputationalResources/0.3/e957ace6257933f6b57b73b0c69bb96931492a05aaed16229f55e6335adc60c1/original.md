```
CPUProcesses()
CPUProcesses(settings)
```

Indicate that a computation should be performed using the CPU in multi-process mode. Processes should be added with addprocs() or julia started with `julia -p N`. Processes must communicate using distributed memory operations such as remote refrences. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(CPUProcesses(), image, kernel)
filter(CPUProcesses(TileSize(64,8)), image, kernel)
```
