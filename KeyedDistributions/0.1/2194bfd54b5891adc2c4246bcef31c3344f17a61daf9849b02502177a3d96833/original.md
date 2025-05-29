```
KeyedDistribution(d::Distribution)
```

Constructs a [`KeyedDistribution`](@ref) using the keys and dimnames of the parameter that matches `size(d)`. If the parameter has no keys, uses `1:n` for the length `n` of each dimension.
