```
MergeGreedy <: CodeSimplifier
MergeGreedy(; threshhold=-1e-12)
```

Contraction code simplifier (in order to reduce the time of calling optimizers) that merges tensors greedily if the space complexity of merged tensors is reduced (difference smaller than the `threshhold`).
