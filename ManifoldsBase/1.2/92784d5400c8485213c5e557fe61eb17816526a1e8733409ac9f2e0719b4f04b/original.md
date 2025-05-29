```
EmbeddedRetraction{T<:AbstractRetractionMethod} <: AbstractRetractionMethod
```

Compute a retraction by using the retraction of type `T` in the embedding and projecting the result.

# Constructor

```
EmbeddedRetraction(r::AbstractRetractionMethod)
```

Generate the retraction with retraction `r` to use in the embedding.
