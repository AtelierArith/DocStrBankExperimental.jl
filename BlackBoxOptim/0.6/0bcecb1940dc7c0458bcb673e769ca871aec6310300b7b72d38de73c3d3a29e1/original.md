```
fitness_improvement_potential(a::Archive[, p = 0.01])
```

Calculate the solution improvement potential.

The percentage improvement that can be expected from the current fitness value at a given `p`-value. In theory, an optimization run should be terminated when this value is very small, i.e. there is little improvement potential left in the run.
