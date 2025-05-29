EmbeddedInverseRetraction{T<:AbstractInverseRetractionMethod} <: AbstractInverseRetractionMethod

Compute an inverse retraction by using the inverse retraction of type `T` in the embedding and projecting the result

# Constructor

```
EmbeddedInverseRetraction(r::AbstractInverseRetractionMethod)
```

Generate the inverse retraction with inverse retraction `r` to use in the embedding.
