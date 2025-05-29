```
squash(g::ValGraph)
squash(g::ValDiGraph)
squash(g::ValOutDiGraph)
```

Return a copy of `g` with an `eltype` as small as possible.

This can help with performance. Only the `eltype` is changed, all other types stay the same.
