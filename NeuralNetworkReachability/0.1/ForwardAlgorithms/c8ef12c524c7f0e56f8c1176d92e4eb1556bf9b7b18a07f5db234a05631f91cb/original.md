```
SplitForward{S<:ForwardAlgorithm,FS,FM} <: ForwardAlgorithm
```

Forward algorithm that splits a set, then computes the image under the neural network, and finally merges the resulting sets again, all according to a policy.

### Fields

  * `algo` – algorithm to be applied between splitting and merging
  * `split_function` – function for splitting
  * `merge_function` – function for merging
