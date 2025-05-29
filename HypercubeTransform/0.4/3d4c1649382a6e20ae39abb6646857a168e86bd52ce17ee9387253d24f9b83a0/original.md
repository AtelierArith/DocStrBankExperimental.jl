```
`ascube(c)
```

Constructs the object that contains the necessary information to move from the unit hypercube to the distribution space. This is the usual function to use when construct the transformation.

There are a few different behaviors depending on the type of the object.

  * If `c::Distribution` then this will store the distributions.
  * If `c::Tuple{AbstractHypercubeTransform}` then this will store the tuple

# Examples

```julia
ascube(Normal())
ascube(MultivariateNormal())
ascube((Normal(), Normal(2.0)))
ascube( (α = Uniform(), β = Normal()) )
```
