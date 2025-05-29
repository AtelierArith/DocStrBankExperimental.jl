```
split_secret(secret::String, n::Int, t::Int; prime_bits::Int=4096)::Vector{String}
```

Split a secret string into n shares, with a threshold of t shares required for reconstruction.

Parameters:

  * secret: The secret string to be split
  * n: The total number of shares to generate
  * t: The minimum number of shares required to reconstruct the secret
  * prime_bits: The number of bits for the prime modulus (default: 2048)

Returns:

  * A vector of serialized share strings
