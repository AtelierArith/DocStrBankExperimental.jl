```
SequentialBatchAM(::AcquisitionMaximizer, ::Int)
SequentialBatchAM(; am, batch_size)
```

Provides multiple candidates for batched objective function evaluation.

Selects the candidates sequentially by iterating the following steps:

  * 1. Use the 'inner' acquisition maximizer to select a candidate `x`.
  * 2. Extend the dataset with a 'speculative' new data point

    created by taking the candidate `x` and the posterior predictive mean of the surrogate `ŷ`.
  * 3. If `batch_size` candidates have been selected, return them.

    Otherwise, goto step 1).

# Keywords

  * `am::AcquisitionMaximizer`: The inner acquisition maximizer.
  * `batch_size::Int`: The number of candidates to be selected.
