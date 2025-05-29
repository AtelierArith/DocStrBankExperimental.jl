```
@ballocations expression [other parameters...]
```

Similar to the `@allocations` macro included with Julia, this macro evaluates an expression, discarding the resulting value, and returns the total number of allocations made during its execution.

Unlike `@allocations`, it uses the `@benchmark` macro from the `BenchmarkTools` package, and accepts all of the same additional parameters as `@benchmark`. The returned number of allocations corresponds to the trial with the *minimum* elapsed time measured during the benchmark.
