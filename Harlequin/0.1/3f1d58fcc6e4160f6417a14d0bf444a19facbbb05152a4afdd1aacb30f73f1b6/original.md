```
mutable struct CleanedTOD{T <: Real}
```

This structure is used to associated a TOD containing some measurement with the set of baselines estimated by the destriper. It implements the iterator interface, which means that it can be used like if it were an array.
