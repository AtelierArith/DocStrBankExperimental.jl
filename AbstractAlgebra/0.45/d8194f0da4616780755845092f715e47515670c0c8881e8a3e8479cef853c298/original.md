```
order(::Type{T} = BigInt, g::GroupElem) where T
```

Return the order of $g$ as an instance of `T`. If $g$ is of infinite order, an `InfiniteOrderError` exception will be thrown. Use `is_finite_order(G)` to avoid this kind of exception. If the order does not fit into type `T`, an `InexactError` exception will be thrown.
