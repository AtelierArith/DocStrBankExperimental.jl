```
SDS([options])
```

Standardized data sphering.

See [`EigenAnalysis`](@ref) for detailed description of the available options.

# Examples

```julia
SDS()
SDS(maxdim=4)
SDS(pratio=0.88)
SDS(maxdim=4, pratio=0.88)
```

## Notes

  * `SDS()` is shortcut for `ZScore() → EigenAnalysis(:VDV)`.
