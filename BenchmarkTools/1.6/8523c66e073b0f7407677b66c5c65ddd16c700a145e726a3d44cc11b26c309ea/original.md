```
@belapsed expression [other parameters...]
```

Similar to the `@elapsed` macro included with Julia, this returns the elapsed time (in seconds) to execute a given expression.   It uses the `@benchmark` macro, however, and accepts all of the same additional parameters as `@benchmark`.  The returned time is the *minimum* elapsed time measured during the benchmark.
