```
resetrange(chains::Chains)
```

Generate a new chain from `chains` with iterations indexed by `1:n`, where `n` is the number of samples per chain.

The new chain and `chains` share the same data in memory.
