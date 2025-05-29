```
TileBuffer(a, inds::Indices) -> v
```

Return a buffer-view `v` whose indices match `inds`, using the array `a` for storage. `inds` does not necessarily have to match the size of `a` (which allows tiles to be of different sizes, e.g., at the edges).
