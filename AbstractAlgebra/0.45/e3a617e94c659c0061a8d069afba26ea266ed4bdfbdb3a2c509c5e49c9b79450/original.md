```
order(::Type{T} = BigInt, G::Group) where T
```

Return the order of $G$ as an instance of `T`. If $G$ is of infinite order, an `InfiniteOrderError` exception will be thrown. Use `is_finite(G)` to avoid this kind of exception. If the order does not fit into type `T`, an `InexactError` exception will be thrown.
