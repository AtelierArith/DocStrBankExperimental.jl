```
interactions(N::AbstractEcologicalNetwork)
```

Returns the interactions in the ecological network. Interactions are returned as an array of named tuples. *A minima*, these have fields `from` and `to`. For networks that are probabilistic, there is a `probability` field. For networks that are quantitative, there is a `strength` field. This functions allows to iterate over interactions in a network in a convenient way.
