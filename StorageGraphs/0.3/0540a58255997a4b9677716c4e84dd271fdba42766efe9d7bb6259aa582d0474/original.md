```
add_nodes!(g, dep::Pair; id=nextid(g))
```

Recursively add nodes via the dependency chain specified by `dep`. If any intermediarry node doesn't exist, it is created. A new path is created starting from the first node to the last one, but if there is an existing part, it is continued (see [`nextid`](@ref)).
