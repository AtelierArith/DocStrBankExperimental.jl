```
optimize_structure!(ff::ForceField)
```

Attempts to solve the energy optimization problem represented by the given force field object.

# Supported keyword arguments

This function passes all keyword arguments to [Optimization.solve](https://docs.sciml.ai/Optimization/stable/API/solve/), with the following default values:

  * `alg = Optimization.LBFGS()`
