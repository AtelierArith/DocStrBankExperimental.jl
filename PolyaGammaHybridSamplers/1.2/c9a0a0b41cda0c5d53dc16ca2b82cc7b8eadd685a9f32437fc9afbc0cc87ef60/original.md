```
rand_pggammasum(b::Real, z::Real, [rng::AbstractRNG = Random.default_rng()])
```

Sample from a Polya-Gamma distribution using the truncated sum of gammas representation.

# Arguments

  * `b::Real`: the shape parameter
  * `z::Real`: the exponential tilting parameter
  * `rng::AbstractRNG`: random number generator object for `rand`

# Returns

  * A sample from the Polya-Gamma distribution with shape parameter `b` and exponential tilting parameter `z`.

# Notes

  * This method supports non-integer `b` but is only an approximation, meant only for b < 1
  * No warning is given if `b` is too large.
  * The sum is truncated to 200 terms according to the paper's recommendation.
  * Automatically selects this method when `b < 1` or when used in combination with the devroye method for non-integer `b`.
