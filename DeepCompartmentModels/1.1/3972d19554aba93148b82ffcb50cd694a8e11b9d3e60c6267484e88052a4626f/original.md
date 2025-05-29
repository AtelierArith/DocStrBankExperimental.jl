```
interpret_branch(model, covariate_idx, anchor, ps, st; x)
```

Returns the output of a specific branch based on dummy input. Can be used to  interpret covariate effects. Returns the unnormalized `x` and the branch output  `y` divided by the prediction at the location of `anchor`:

```julia
y = f(x) ./ f(anchor)
```

# Arguments:

  * `ann`: Lux model.
  * `ps`: Model parameters.
  * `st`: Model state.
  * `covariate_idx`: Index of the covariate in the input vector.
  * `anchor`: Unnormalized covariate value to which the output is "anchored", i.e. f(anchor) = 1.
  * `x`: Normalized dummy input to the branch.
