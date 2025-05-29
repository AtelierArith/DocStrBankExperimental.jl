```
struct Sample
    evals              ::Float64 # The number of times the benchmark was evaluated for this sample.
    time               ::Float64 # The average time taken to run the sample, in seconds per evaluation.
    allocs             ::Float64 # The average number of allocations made per evaluation
    bytes              ::Float64 # The average number of bytes allocated per evaluation
    gc_fraction        ::Float64 # The fraction of time spent in garbage collection (0.0 to 1.0)
    compile_fraction   ::Float64 # The fraction of time spent compiling (0.0 to 1.0)
    recompile_fraction ::Float64 # The fraction of compile time which was, itself, recompilation (0.0 to 1.0)
    warmup             ::Float64 # Whether this sample had a warmup run before it (1.0 = yes. 0.0 = no).
    ...more fields may be added...
end
```

A struct representing a single sample of a benchmark.

[`@b`](@ref) returns a composite sample formed by taking the field-wise minimum of the measured samples. More fields may be added in the future as more information becomes available.
