```
ThreadedCPU <: CPU

ThreadedCPU()
```

[`Processor`](@ref) flag that specifies to use a `Threads.nthreads()` CPUs.

Specifiy with:

```julia
ruleset = Ruleset(rule; proc=ThreadedCPU())
# or
output = sim!(output, rule; proc=ThreadedCPU())
```
