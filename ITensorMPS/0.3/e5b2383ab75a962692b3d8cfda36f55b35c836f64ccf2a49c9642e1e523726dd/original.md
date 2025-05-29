```
random_mps(sites::Vector{<:Index}, state; linkdims=1)
```

Construct a real, random MPS with link dimension `linkdims`, made by randomizing an initial product state specified by `state`. This version of `random_mps` is necessary when creating QN-conserving random MPS (consisting of QNITensors). The initial `state` array provided determines the total QN of the resulting random MPS.
