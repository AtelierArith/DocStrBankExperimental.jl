```
CPU1()
CPU1(settings)
```

Indicate that a computation should be performed using the CPU in single-threaded mode. Optionally pass in an object specifying algorithmic settings.

# Examples:

```julia
filter(CPU1(), image, kernel)
filter(CPU1(TileSize(64,8)), image, kernel)
```
