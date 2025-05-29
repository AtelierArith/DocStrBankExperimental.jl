```
chemicalname(chemical::T; kwargs...)
```

Get name of `chemical`. It is equivalent to `getchemicalattr(chemical, :name; kwargs...)` except that it returns `string("::", T)` when name is not available.
