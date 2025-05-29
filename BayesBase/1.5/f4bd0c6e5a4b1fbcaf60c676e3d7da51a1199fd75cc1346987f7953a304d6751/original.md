```
samplefloattype(distribution)
```

Returns a type of the distribution or the underlying float type in case if sample is `Multivariate` or `Matrixvariate`.  By default fallbacks to the `deep_eltype(sampletype(distribution))`.

See also: [`sampletype`](@ref), [`promote_sampletype`](@ref), [`promote_samplefloattype`](@ref)
