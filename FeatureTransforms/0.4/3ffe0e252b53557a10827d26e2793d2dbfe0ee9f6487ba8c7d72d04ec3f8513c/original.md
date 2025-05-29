```
OneHotEncoding{R<:Real} <: Transform
```

One-hot encode the categorical value for each target element.

Construct a n-by-p binary matrix, given a `Vector` of target data `x` (of length n) and a `Vector` of all unique possible values in x (of length p).

The element [i, j] is `true` if the i^th target in `x` corresponds to the j^th possible value and `false` otherwise. Note that `R`can be specified to determine the return type of results. It defaults to a `Matrix` of `Bool`s.

Note that this Transform does not support specifying dims other than `:` (all dims) because it is a one-to-many transform (for example a `Vector` input produces a `Matrix` output).

Note that `OneHotEncoding` needs to be first encoded with the expected categories before it can be used. This is because the data might be missing certain categories which will lead to incomplete classification.
