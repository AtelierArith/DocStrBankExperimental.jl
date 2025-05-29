```
get_score(feature::HaarLikeObject, int_img::AbstractArray) -> Tuple{Number, Number}
```

Get score for given integral image array.  This is the feature cascade.

# Arguments

  * `feature::HaarLikeObject`: given Haar-like feature (parameterised replacement of Python's `self`)
  * `int_img::AbstractArray`: Integral image array

# Returns

  * `score::Number`: Score for given feature
