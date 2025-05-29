```
tune!(b::Benchmark, p::Parameters = b.params; verbose::Bool = false, pad = "", kwargs...)
```

Tune a `Benchmark` instance.

If the number of evals in the parameters `p` has been set manually, this function does nothing.
