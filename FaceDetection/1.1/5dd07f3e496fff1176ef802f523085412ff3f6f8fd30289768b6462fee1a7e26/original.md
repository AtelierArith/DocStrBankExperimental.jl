```
get_faceness(feature::HaarLikeObject{I, F}, int_img::IntegralArray{T, N}) -> Number
```

Get facelikeness for a given feature.

# Arguments

  * `feature::HaarLikeObject`: given Haar-like feature (parameterised replacement of Python's `self`)
  * `int_img::IntegralArray`: Integral image array

# Returns

  * `score::Number`: Score for given feature
