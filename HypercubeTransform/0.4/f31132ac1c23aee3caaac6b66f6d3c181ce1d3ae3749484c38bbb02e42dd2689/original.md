```
transform(c::AbstractHypercubeTransform, p)
```

Transforms from the hypercube with coordinates `p`, to the parameter space defined by the transformation `c`.

The behavior of this function depends on the nature of `c`.

  * If `c` is a <: Distributions.Distributions and has a quantile method

this will just call the quantile function. If no quantile function is defined then a custom transformation depending on the type of `c` will be called. If no custom transformation exists then an error will be raised.

  * If `c` is a Tuple of transformations then transform will iterate through the

tuple using a similar method to the  [TransformVariables.jl](https://github.com/tpapp/TransformVariables.jl) method.
