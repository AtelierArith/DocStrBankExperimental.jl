```
ClipScale(ϵ = 1e-5)
```

Projection operator ensuring that an `MvLocationScale` or `MvLocationScaleLowRank` has a scale with eigenvalues larger than `ϵ`. `ClipScale` also supports by operating on `MvLocationScale` and `MvLocationScaleLowRank` wrapped by a `Bijectors.TransformedDistribution` object. 
