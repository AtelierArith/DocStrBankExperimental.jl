```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

Return the [`InverseProductRetraction`](@ref) For two or more [`AbstractInverseRetractionMethod`](@ref)s, where for the case that one of them is a [`InverseProductRetraction`](@ref) itself, the other is either prepended (if `r` is a product) or appenden (if `s`) is. If both [`InverseProductRetraction`](@ref)s, they are combined into one keeping the order.
