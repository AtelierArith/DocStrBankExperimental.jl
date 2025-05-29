```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

Return the [`ProductRetraction`](@ref) For two or more [`AbstractRetractionMethod`](@ref)s, where for the case that one of them is a [`ProductRetraction`](@ref) itself, the other is either prepended (if `m` is a product) or appenden (if `n`) is. If both [`ProductRetraction`](@ref)s, they are combined into one keeping the order.
