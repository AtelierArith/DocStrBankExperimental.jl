```
concat(name::AbstractString, v::AbstractVertex, vs::AbstractVertex...; traitfun=identity, layerfun=identity)
```

Return a vertex with name `name` which concatenates input along the activation (e.g. channel if convolution, first dimension if dense) dimension.

Name is only used when displaying or logging and does not have to be unique (although it probably is a good idea).

Inputs must have compatible activation shapes or an exception will be thrown.

Keyword argument `layerfun` can be used to wrap the computation, e.g. in an [`ActivationContribution`](@ref). 

Keyword argument `traitfun` can be used to wrap the `MutationTrait` of the vertex in a `DecoratingTrait`

See also `NaiveNASlib.conc`. 
