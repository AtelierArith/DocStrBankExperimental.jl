```
cross(O1::AbstractGroupOperation, O2::AbstractGroupOperation)
O1 × O2
O1 × O2 × O3 × ...
```

Return the [`ProductGroupOperation`](@ref) For two [AbstractGroupOperation`](@ref) `O1` and `O2`, where for the case that one of them is a [`ProductGroupOperation`](@ref) itself, the other is either prepended (if `O1` is a product) or appended (if `O2` is). If both are product operations, they are combined into one, keeping the order of operations.

For the case that more than two are concatenated with `×` this is iterated.
