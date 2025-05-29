```
`inverse(c::AbstractHypercubeTransform, p)`
```

Transforms from the parameter space `p`, to the unit hypercube defined by the transformation `c`.

The behavior of this function depends on the nature of `c`.

  * If `c` is a <: Distributions.Distributions and has a cdf method

this will just call the cdf function. If no cdf function is defined then a custom transformation depending on the type of `c` will be called. If no custom transformation exists then an error will be raised.

  * If `c` is a Tuple of transformations then inverse will iterate through the

tuple using a similar method to the  [TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl) method.
