```
spring_layout(g; 
              k = 1 / √nv(g),
              maxiter = 100,
              inittemp = 2.0,
              [x0, y0]) -> x, y
```

Return the positions of the nodes in graph `g` according to  Fruchterman and Reingold's spring/repulsion model. The forces as function of the distance `d` beetween two nodes  are given by

```
f_a(d) =  d / k # attractive force
f_r(d) = -k^2 / d^2 # repulsive force:
```

`maxiter` is the number of updates of the positions.  `inittemp` controls displacement per iteration.

Initial positions can passed though the argument `x0` and `y0`.

The positions are rescaled to fit the [-1, +1]^2 box. 

This function is adapted from [GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl).
