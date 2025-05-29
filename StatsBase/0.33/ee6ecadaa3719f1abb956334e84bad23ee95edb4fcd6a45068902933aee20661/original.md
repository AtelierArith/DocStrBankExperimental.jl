```
mode(a, [r])
mode(a::AbstractArray, wv::AbstractWeights)
```

Return the mode (most common number) of an array, optionally over a specified range `r` or weighted via a vector `wv`. If several modes exist, the first one (in order of appearance) is returned.
