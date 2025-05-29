```
DRS([options])
```

Dimension reduction sphering.

See [`EigenAnalysis`](@ref) for detailed description of the available options.

# Examples

```julia
DRS(maxdim=3)
DRS(pratio=0.87)
DRS(maxdim=3, pratio=0.87)
```

## Notes

  * `DRS()` is shortcut for `ZScore() → EigenAnalysis(:VD)`.
