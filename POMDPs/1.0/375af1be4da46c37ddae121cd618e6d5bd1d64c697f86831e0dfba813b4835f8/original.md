```
currentobs(b)
```

Return the latest observation associated with belief `b`.

If a solver or updater implements `history(b)` for a belief type, `currentobs` has a default implementation.
