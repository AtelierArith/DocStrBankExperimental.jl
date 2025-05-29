```
isdegenerate(N::AbstractEcologicalNetwork)
```

Networks are called degenerate if some species have no interactions, either at all, or with any species other than themselves. This is particularly useful to decide the networks to keep when generating samples for null models.
