```
NoiseMap{T,N,R,F}
```

An `N`-dimensional infinite stream of random values.

# Fields

  * `noise` an noise function used to generate the base stream of random numbers
  * `transform` a function that is applied to the output of the noise function to obtain the result

Transforms can be

  * Arbitrary functions
  * An instance of `NoiseUniform`, in which case, the values are floating point numbers uniformly distributed in the interval [0,1).
  * An instance of `Distributions.UnivariateDistribution`, in which case the values are samples from that distribution.

# Examples

```jldoctest
julia> nm = NoiseMap(sqn)
NoiseMap{UInt32, 1, SquirrelNoise5, typeof(identity)}(SquirrelNoise5(0x00000000), identity)
```
