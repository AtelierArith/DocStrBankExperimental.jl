```
nextid(g, dep::Pair)
```

Find the next available id such that a dead end (a node with no outgoing paths) along the dependency chain (`dep`) is continued. If there is no such case, it gives the maximum id (see [`walkdep`](@ref)).
