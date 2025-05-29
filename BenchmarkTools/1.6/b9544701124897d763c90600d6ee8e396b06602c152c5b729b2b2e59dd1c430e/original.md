```
@ballocated expression [other parameters...]
```

Similar to the `@allocated` macro included with Julia, this returns the number of bytes allocated when executing a given expression.   It uses the `@benchmark` macro, however, and accepts all of the same additional parameters as `@benchmark`.  The returned allocations correspond to the trial with the *minimum* elapsed time measured during the benchmark.
