```
benchmark_model(model::Turing.Model; suite_kwargs..., kwargs...)
```

Create and run a benchmark suite for `model`.

The benchmarking suite will be created using [`make_turing_suite`](@ref). See [`make_turing_suite`](@ref) for the available keyword arguments and more information.

# Keyword arguments

  * `suite_kwargs`: Keyword arguments passed to [`make_turing_suite`](@ref).
  * `kwargs`: Keyword arguments passed to `BenchmarkTools.run`.
