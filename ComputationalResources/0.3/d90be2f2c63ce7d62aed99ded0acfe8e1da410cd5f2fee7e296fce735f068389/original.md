```
CPUThreads()
CPUThreads(settings)
```

Indicate that a computation should be performed using the CPU in multi-threaded mode. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(CPUThreads(), image, kernel)
filter(CPUThreads(TileSize(64,8)), image, kernel)
```
