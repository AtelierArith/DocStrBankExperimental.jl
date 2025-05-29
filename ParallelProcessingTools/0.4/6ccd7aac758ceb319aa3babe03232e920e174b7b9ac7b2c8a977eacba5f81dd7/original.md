```
@onprocs procsel expr
```

Executes `expr` in parallel on all processes in `procsel`. Waits until all processes are done. Returns all results as a vector (or as a single scalar value, if `procsel` itself is a scalar).

Example:

```julia
using Distributed
addprocs(2)
workers() == @onprocs workers() myid()
```
