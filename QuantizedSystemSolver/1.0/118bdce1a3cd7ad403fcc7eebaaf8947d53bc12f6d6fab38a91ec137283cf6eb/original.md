```
powerT(a::T, r::S, cache1::Taylor0) where {S<:Real,T<:Number}
```

Raises `a` to the power `r` and stores the result in `cache1`.

# Arguments

  * `a::T`: The base, a number.
  * `r::S`: The exponent, a real number.
  * `cache1::Taylor0`: The cache to store the result.

# Returns

  * `cache1::Taylor0`: The result of `a^r`.
