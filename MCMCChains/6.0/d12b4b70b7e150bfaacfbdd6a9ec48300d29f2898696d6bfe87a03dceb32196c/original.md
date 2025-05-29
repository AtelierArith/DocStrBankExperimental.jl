```
setrange(chains::Chains, range::AbstractVector{Int})
```

Generate a new chain from `chains` with iterations indexed by `range`.

The new chain and `chains` share the same data in memory.
