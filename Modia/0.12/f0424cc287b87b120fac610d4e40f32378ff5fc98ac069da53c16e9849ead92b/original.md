```
leq = initLinearEquationsIteration!(m::InstantiatedModel, leq_index::Int)
```

Initialize iteration over linear equations system of index `leq_index` and return a reference to it that can be used in the while-loop to construct and solve the linear equation system.
