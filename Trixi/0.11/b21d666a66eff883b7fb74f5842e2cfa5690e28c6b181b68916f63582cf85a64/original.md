```
velocity(u, equations)
```

Return the velocity vector corresponding to the equations, e.g., fluid velocity for Euler's equations. The velocity in certain orientation or normal direction (scalar) can be computed with `velocity(u, orientation, equations)` or `velocity(u, normal_direction, equations)` respectively. The `velocity(u, normal_direction, equations)` function calls `velocity(u, equations)` to compute the velocity vector and then normal vector, thus allowing a general function to be written for the AbstractEquations type. However, the `velocity(u, orientation, equations)` is written for each equation separately to ensure only the velocity in the desired direction (orientation) is computed. `u` is a vector of the conserved variables at a single node, i.e., a vector of the correct length `nvariables(equations)`.
