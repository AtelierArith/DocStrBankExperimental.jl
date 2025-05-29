```
solve!( problem :: Problem; verbose=true )
```

Solve (i.e. integrate in time) an initial-value problem

The argument `problem` should be of type `Problem`. It may be buit, e.g., by `Problem(model, initial, param)`

Information are not printed if keyword argument `verbose = false` (default is `true`).
