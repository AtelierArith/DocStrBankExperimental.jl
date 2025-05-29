```
fluxvertex(l, in::AbstractVertex; layerfun=LazyMutable, traitfun=validated())
```

Return a vertex which wraps the layer `l` and has input vertex `in`.

Keyword argument `layerfun` can be used to wrap the computation, e.g. in an [`ActivationContribution`](@ref). 

Keyword argument `traitfun` can be used to wrap the `MutationTrait` of the vertex in a `DecoratingTrait`
