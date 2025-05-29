```
concat(v::AbstractVertex, vs::AbstractVertex...; traitfun=identity, layerfun=identity)
```

Return a vertex which concatenates input along the activation (e.g. channel if convolution, first dimension if dense) dimension.

Inputs must have compatible activation shapes or an exception will be thrown.

Keyword argument `layerfun` can be used to wrap the computation, e.g. in an [`ActivationContribution`](@ref). 

Keyword argument `traitfun` can be used to wrap the `MutationTrait` of the vertex in a `DecoratingTrait`

See also `NaiveNASlib.conc`. 
