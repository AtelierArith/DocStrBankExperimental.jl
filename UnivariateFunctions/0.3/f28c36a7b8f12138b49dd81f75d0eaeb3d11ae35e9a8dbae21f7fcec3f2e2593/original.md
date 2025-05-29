```
convert_to_linearly_rescale_inputs(f::UnivariateFunction, alpha::Real, beta::Real)
```

This alters a function so that whenever we put in x it is like we put in `alpha * x + beta`.

### Inputs

  * `f` - A `UnivariateFunction`.
  * `alpha` - The slope of the rescaling.
  * `beta` - The level of the rescaling.

### Returns

  * A `UnivariateFunction` of the type that you input to the function.
