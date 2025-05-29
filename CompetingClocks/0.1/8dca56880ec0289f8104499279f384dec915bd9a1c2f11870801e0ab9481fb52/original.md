```
SSA{KeyType,TimeType}
```

This abstract type represents a stochastic simulation algorithm (SSA). It is parametrized by the clock ID, or key, and the type used for the time, which is typically a Float64. The type of the key can be anything you would use as a dictionary key. This excludes mutable values but includes a wide range of identifiers useful for simulation. For instance, it could be a `String`, but it could be a `Tuple{Int64,Int64,Int64}`, so that it indexes into a complicated simulation state.
