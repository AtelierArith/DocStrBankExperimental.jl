```
@btimed expression [other parameters...]
```

Similar to the `@timed` macro included with Julia, this macro executes an expression and returns a `NamedTuple` containing the value of the expression, the minimum elapsed time in seconds, the total bytes allocated, the number of allocations, and the garbage collection time in seconds during the benchmark.

Unlike `@timed`, it uses the `@benchmark` macro from the `BenchmarkTools` package for more detailed and consistent performance measurements. The elapsed time reported is the minimum time measured during the benchmark. It accepts all additional parameters supported by `@benchmark`.
