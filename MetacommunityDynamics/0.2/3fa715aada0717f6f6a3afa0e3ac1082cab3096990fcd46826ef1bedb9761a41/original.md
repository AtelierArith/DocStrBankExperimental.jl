```
Coordinates(; coords = nothing, env = nothing)
```

Builds a `Coordinates`, where both the coordinates and the environmental variables can be passed as keyword arguments. The environment should be a dictionary where (key,value) pairs are names of each environmnetal variable and vectors of that variable across each node in the `Coordinates`.
