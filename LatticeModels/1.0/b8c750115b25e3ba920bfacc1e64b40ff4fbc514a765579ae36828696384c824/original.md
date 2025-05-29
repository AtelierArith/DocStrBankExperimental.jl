```
removedangling!(lat[, maxdepth])
```

Remove dangling sites from the lattice. A site is considered dangling if it has less than 2 neighbors. The function will remove all dangling sites and their neighbors recursively up to `maxdepth` levels — the default is `Inf`.
