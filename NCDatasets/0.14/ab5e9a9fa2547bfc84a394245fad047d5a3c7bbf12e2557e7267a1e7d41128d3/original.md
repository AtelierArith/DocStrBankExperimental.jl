```
names = dimnames(ds::AbstractNCDataset; parents = false)
```

Return all names defined in `ds`. When `parents` is `true`, also the names of parent groups are returned (default is `false`).
