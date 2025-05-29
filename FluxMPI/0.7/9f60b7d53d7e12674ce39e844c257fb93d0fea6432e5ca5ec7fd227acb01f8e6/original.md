```
DistributedOptimizer(optimizer)
```

Wrap the `optimizer` in a `DistributedOptimizer`. Before updating the parameters, this adds the gradients across the processes using non-blocking Allreduce

## Arguments

  * `optimizer`: An Optimizer compatible with the Optimisers.jl package

!!! note
    Remember to scale the loss function by `1 / total_workers()` to ensure that the gradients are correctly averaged

