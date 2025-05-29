```
range = inputrange(P::AbstractProcess)
```

Return the range of inputs (control signals) of the process. `range` is a vector of tuples, `length(range) = num_inputs(P), eltype(range) = Tuple(Real, Real)`
