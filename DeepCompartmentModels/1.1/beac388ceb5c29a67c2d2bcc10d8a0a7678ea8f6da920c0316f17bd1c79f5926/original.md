```
interpret_branch(model, covariate_idx, anchor; x)
```

Convenience function for running the interpretation function on models following  the AbstractModel interface.

# Arguments:

  * `model::AbstractModel`: AbstractModel (e.g. DeepCompartmentModel(...)) using an Multi-branch based neural network.
  * `covariate_idx`: Index of the covariate in the input vector.
  * `anchor`: Unnormalized covariate value to which the output is "anchored", i.e. f(anchor) = 1.
  * `x`: Normalized dummy input to the branch.
