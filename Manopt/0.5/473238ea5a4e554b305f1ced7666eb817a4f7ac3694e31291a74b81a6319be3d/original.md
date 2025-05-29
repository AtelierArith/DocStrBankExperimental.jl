```
ScaledManifoldObjective{E, O2, O1<:AbstractManifoldObjective{E},F} <:
   AbstractDecoratedManifoldObjective{E,O2}
```

Declare an objective to be defined as a scaled version of an existing objective.

This rescales all involved functions.

For now the functions rescaled are

  * the cost
  * the gradient
  * the Hessian

# Fields

  * `objective`: the objective that is defined in the embedding
  * `scale=1`: the scaling applied

# Constructors

```
ScaledManifoldObjective(objective, scale::Real=1)
-objective
scale*objective
```

Generate a scaled manifold objective based on `objective` with `scale` being `1` by default in the first, `scale=-1` in the second case. The multiplication from the left with a scalar is also overloaded.
