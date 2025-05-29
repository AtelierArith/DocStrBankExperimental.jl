```
struct StorCap <: AbstractStorageParameters
```

A storage parameter type for including only a capacity. This implies that neither the usage of the [`Storage`](@ref), nor the installed capacity have a direct impact on the objective function.

# Fields

  * **`capacity::TimeProfile`** is the installed capacity.
