```
NLLSsolver.nullcallback(cost, problem, data, iteratedata)
```

A callback that does nothing and returns the tuple `(cost, 0)`.

# Example

Optimizing an NLLSsolver problem as follows:

```julia
    NLLSsolver.optimize!(problem, options, unfixed, nullcallback)
```

will incur no callback overhead.

!!! note
    This is the default callback used by `optimize!`.

