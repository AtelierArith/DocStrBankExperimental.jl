```julia
inpctile(A, p::Number; dims)
```

Return a boolean array that identifies which values of the iterable collection `A` fall within the central `p`th percentile, optionally along a dimension specified by `dims`.

A valid percentile value must satisfy `0 <= p <= 100`.
