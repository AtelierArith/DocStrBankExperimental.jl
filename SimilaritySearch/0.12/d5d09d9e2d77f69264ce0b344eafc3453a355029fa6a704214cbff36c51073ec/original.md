```
getminbatch(minbatch, n)
```

Used by functions that use parallelism based on `Polyester.jl` minibatches specify how many queries (or something else) are solved per thread whenever the thread is used (in minibatches). 

# Arguments

  * `minbatch`

      * Integers $1 ≤ minbatch ≤ n$ are valid values (where n is the number of objects to process, i.e., queries)
      * Defaults to 0 which computes a default number based on the number of available cores and `n`.
      * Set `minbatch=-1` to avoid parallelism.
