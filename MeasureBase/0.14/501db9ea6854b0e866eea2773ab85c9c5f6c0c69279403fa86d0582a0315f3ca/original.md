`paramnames(μ)` returns the names of the parameters of `μ`. This is equivalent to 

```
paramnames(μ) == (keys ∘ params)(μ)
```

but depends only on the type. In particular, the default implementation is

```
paramnames(μ::M) where {M} = paramnames(M)
```

New `ParameterizedMeasure`s will automatically have a `paramnames` method. For other measures, this method is optional, but can be added by defining

```
paramnames(::Type{M}) where {M} = ...
```

See also `params`
