```
fcialg(n::V, I, par...; augmented=true, verbose=false, kwargs...)
```

Perform the FCI algorithm for a set of `n` variables using the test

```
I(u, v, [s1, ..., sn], par...)
```

Returns the PAG as a MetaDiGraph
