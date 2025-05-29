```
reset!(brkga_data::BrkgaData)
```

Reset all populations with brand new keys. All warm-start solutions provided by [`set_initial_population!`](@ref) are discarded. You may use [`inject_chromosome!`](@ref) to insert those solutions again.

!!! warning
    As it is in [`evolve!()`](@ref), the decoding is done in parallel using threads, and the user **must guarantee that the decoder is THREAD-SAFE.** If such property cannot be held, we suggest using single thread by setting the environmental variable `JULIA_NUM_THREADS = 1` [(see Julia Parallel Computing)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/)


# Throws

  * `ErrorException`: if [`initialize!`](@ref) has not been called before.
