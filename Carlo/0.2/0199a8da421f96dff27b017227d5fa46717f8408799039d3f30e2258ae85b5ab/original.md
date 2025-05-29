```
ParallelTemperingMC <: AbstractMC
```

An implementation of the [parallel run mode](@ref parallel_run_mode) `AbstractMC` interface that runs other `AbstractMC` implementations with parallel tempering.

The child implementation is expected to implement

  * [`parallel_tempering_log_weight_ratio`](@ref)
  * [`parallel_tempering_change_parameter!`](@ref)
