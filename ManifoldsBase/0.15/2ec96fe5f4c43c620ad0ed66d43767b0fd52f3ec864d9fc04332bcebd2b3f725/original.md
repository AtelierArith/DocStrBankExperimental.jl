```
×(m, n)
cross(m, n)
cross(m1, m2, m3,...)
```

Return the [`ProductVectorTransport`](@ref) For two or more [`AbstractVectorTransportMethod`](@ref)s, where for the case that one of them is a [`ProductVectorTransport`](@ref) itself, the other is either prepended (if `r` is a product) or appenden (if `s`) is. If both [`ProductVectorTransport`](@ref)s, they are combined into one keeping the order.
