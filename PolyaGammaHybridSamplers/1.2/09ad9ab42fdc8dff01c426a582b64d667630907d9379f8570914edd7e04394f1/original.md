```
rand_pgdevroye(b::Integer, z::Real, [rng::AbstractRNG = Random.default_rng()]])
```

Sample from a Polya-Gamma distribution using the Devroye method.

# Arguments

  * `b::Integer`: the shape parameter
  * `z::Real`: the exponential tilting parameter
  * `rng::AbstractRNG`: optional random number generator object for `rand`

# Returns

  * A sample from the Polya-Gamma distribution with shape parameter `b` and exponential tilting parameter `z`.

# Notes

  * This method is exact, but is increasingly slower as `b` increases.
  * This sampler requires integer `b`.
  * Automatically selects the method when `b < 13` and is an integer.
