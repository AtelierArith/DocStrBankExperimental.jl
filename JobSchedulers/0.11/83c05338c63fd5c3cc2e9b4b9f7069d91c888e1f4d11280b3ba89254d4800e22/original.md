```
set_scheduler_max_cpu(ncpu::Int = default_ncpu())
set_scheduler_max_cpu(percent::Float64)
```

Set the maximum CPU (thread) the scheduler can use. If starting Julia with multiple threads in the default thread pool, the maximum CPU is the number of tids in the default thread pool not equal to 1.

# Example

```
set_scheduler_max_cpu()     # use all available CPUs
set_scheduler_max_cpu(4)    # use 4 CPUs
set_scheduler_max_cpu(0.5)  # use 50% of CPUs
```
