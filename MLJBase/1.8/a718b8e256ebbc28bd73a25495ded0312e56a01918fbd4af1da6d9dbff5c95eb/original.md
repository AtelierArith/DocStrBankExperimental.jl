```
nrows_at_source(N::node)
```

Return the number of rows of data wrapped at the source of `N`, assumming this is unique.

Not to be confused with `J = nrows(N)`, which is a new node such that `J() = nrows(N())`.

See also [`nrows`](@ref)
