```
evolve!(brkga_data::BrkgaData, num_generations::Int64 = 1)
```

Evolve the current populations following the guidelines of Multi-parent BRKGAs for `num_generations` generations.

!!! warning
    The decoding is done in parallel using threads, and the user **must guarantee that the decoder is THREAD-SAFE.** If such property cannot be held, we suggest using single thread by setting the environmental variable `JULIA_NUM_THREADS = 1` [(see Julia Parallel Computing)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/).


# Throws

  * `ErrorException`: if [`initialize!()`](@ref) was not called before.
  * `ArgumentError`: when `num_generations < 1`.
