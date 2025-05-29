```
similar_(name, A)     ≈ similar(A)
Array_{T}(name, size) ≈ Array{T}(undef, size)
```

New arrays for intermediate results, drawn from an LRU cache when `length(A) >= 2000`. The cache's key uses `name::Symbol` as well as type & size to ensure different uses don't collide.

```
copy_(name, A) = copyto!(similar_(name, A), A)
```

Just like that.
