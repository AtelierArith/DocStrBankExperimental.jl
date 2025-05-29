```
nvmon(f, group_or_groups[; gpuids])
```

Monitor performance groups while executing the given function `f` on one or multiple GPUs. Note that

  * `NvMon.init` and `NvMon.finalize` are called automatically
  * the measurement of multiple performance groups is sequential and requires multiple executions of `f`!

**Keyword arguments:**

  * `gpuids` (default: first GPU): specify the GPUs to be monitored

**Note: This is an experimental feature and might change or be dropped any time!**

# Example

```julia
julia> using LIKWID

julia> x = CUDA.rand(1000); y = CUDA.rand(1000);

julia> metrics, events = nvmon("FLOPS_DP") do
           CUDA.@sync x .+ y;
       end;
```
