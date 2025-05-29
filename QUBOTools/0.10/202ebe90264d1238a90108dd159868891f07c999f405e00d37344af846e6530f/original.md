```
reads(model)
reads(solution::AbstractSolution)
```

Returns the total amount of reads from each sample, combined.

```
reads(model, i::Integer)
reads(solution::AbstractSolution, i::Integer)
```

Returns the sampling frequency of the $i$-th sample on the model's current solution, if available.
