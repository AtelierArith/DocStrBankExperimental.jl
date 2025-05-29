```
range = outputrange(P::AbstractProcess)
```

Return the range of outputs (measurement signals) of the process. `range` is a vector of tuples,  `length(range) = num_outputs(P), eltype(range) = Tuple(Real, Real)`
