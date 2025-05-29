```
ChainedTransform{T1, T2}
```

A transformer that applies, in sequence, a pair of other transformers. This can be used to, for example, do a PCA then a z-score on the projected space. This is limited to two steps because the value of chaining more transformers is doubtful. We may add support for more complex transformations in future versions.

The first and second steps are accessible through `first` and `last`.
