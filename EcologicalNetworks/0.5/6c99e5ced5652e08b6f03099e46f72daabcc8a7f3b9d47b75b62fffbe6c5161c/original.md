```
has_interaction(N::AbstractEcologicalNetwork, i::Int64, j::Int64)
```

This function returns `true` if the interaction between `i` and `j` is not 0. This refers to species by their position instead of their name, and is not recommended as the main solution. This is used internally by a few functions, but is exported because it may be of general use.
