```
brownians_in_use(itos::Array{ItoIntegral,1}, brownians::Array{Symbol,1})
```

Determine which Browninan processes are used in an array of `ItoIntegral`s.

### Inputs

  * itos - A dict containing each of the ito integrals
  * brownians - All possible brownians

### Outputs

  * A `Vector` of what brownians are in use in itos
  * A `Vector` with the indices of these brownians.
