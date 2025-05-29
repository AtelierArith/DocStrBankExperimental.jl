```
PCA([options])
```

Principal component analysis.

See [`EigenAnalysis`](@ref) for detailed description of the available options.

# Examples

```julia
PCA(maxdim=2)
PCA(pratio=0.86)
PCA(maxdim=2, pratio=0.86)
```

## Notes

  * `PCA()` is shortcut for `ZScore() → EigenAnalysis(:V)`.
