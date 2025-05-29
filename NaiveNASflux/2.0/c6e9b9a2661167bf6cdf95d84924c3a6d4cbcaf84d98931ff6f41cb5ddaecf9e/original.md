```
fluxvertex(name::AbstractString, l, in::AbstractVertex; layerfun=LazyMutable, traitfun=validated())
```

Return a vertex with name `name` which wraps the layer `l` and has input vertex `in`.

Name is only used when displaying or logging and does not have to be unique (although it probably is a good idea).

Keyword argument `layerfun` can be used to wrap the computation, e.g. in an [`ActivationContribution`](@ref). 

Keyword argument `traitfun` can be used to wrap the `MutationTrait` of the vertex in a `DecoratingTrait`
