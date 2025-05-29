```
final_neighborhs(g, dep::Pair; dir=:out)
```

Return the vertex indices for the neighbors at the end of the dependency chain. Note: this assumes that the dependency chain is valid (all the nodes exist).
