```
pmapreduce(f, op, [::AbstractWorkerPool], c...; algorithm = :even)
```

A parallel version of the function `mapreduce` using available workers, where `f` is applied to each element in `c`, and the result is reduced using `op`.

There are three choices for `algorithm`:

  * `:even`, evenly partitions the elements in `c` across workers, see `@distributed`.
  * `:reduction_local`, the elements in `c` are asynchronously distributed to the workers. Each element is sent to the next available worker. The result of `f` is reduced and stored locally. When `c` is exhausted, the local results are sent back to the master, who makes the final reduction.
  * `:reduction_master`, similar to `:reduction_local`, but the result of each computation of `f` is sent back to the master, where all reductions are made.
