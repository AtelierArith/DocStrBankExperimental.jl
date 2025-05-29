```
dicg_maximum_step(lmo, direction, x)
```

Given `x` the current iterate and `direction` the negative of the direction towards which the iterate will move, determine a maximum step size `gamma_max`, such that `x - gamma_max * direction` is in the polytope.
