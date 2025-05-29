```
empty!!(vi::AbstractVarInfo)
```

Empty the fields of `vi.metadata` and reset `vi.logp[]` and `vi.num_produce[]` to zeros.

This is useful when using a sampling algorithm that assumes an empty `vi`, e.g. `SMC`.
