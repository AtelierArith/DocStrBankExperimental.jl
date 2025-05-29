```
vars(fp::AbstractFlowpipe)
```

Return the tuple of variable indices of the flowpipe.

### Input

  * `fp` – flowpipe

### Output

Tuple of integers with the variable indices of the flowpipe, typically $1, 2, …, n$ where $n$ is the dimension of the flowpipe.

### Notes

The fallback implementation assumes first reach-set is representative.
