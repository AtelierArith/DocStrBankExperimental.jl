```
get_vote(feature::HaarLikeObject, int_img::IntegralArray) -> Integer
```

Get vote of this feature for given integral image.

# Arguments

  * `feature::HaarLikeObject`: given Haar-like feature
  * `int_img::IntegralArray`: Integral image array

# Returns

  * `vote::Integer`:  1       ⟺ this feature votes positively  -1      otherwise
