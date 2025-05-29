```
initialize!(brkga_data::BrkgaData)
```

Initialize the populations and others data structures of the BRKGA. If an initial population is supplied, this method completes the remaining individuals, if they do not exist.

!!! warning
    THIS METHOD MUST BE CALLED BEFORE ANY OPTIMIZATION METHODS.


This method also performs the initial decoding of the chromosomes. Therefore, depending on the decoder implementation, this can take a while, and the user may want to time such procedure in his/her experiments.

!!! note
    As it is in [`evolve!`](@ref), the decoding is done in parallel using threads, and the user **must guarantee that the decoder is THREAD-SAFE.** If such property cannot be held, we suggest using a single thread by setting the environmental variable `JULIA_NUM_THREADS = 1` [(see Julia Parallel Computing)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/).


# Throws

  * `ErrorException`: if `bias_function` is not defined previously.
