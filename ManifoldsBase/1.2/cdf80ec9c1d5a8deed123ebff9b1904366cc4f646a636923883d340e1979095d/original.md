```
EmbeddedVectorTransport{T<:AbstractVectorTransportMethod} <: AbstractVectorTransportMethod
```

Compute a vector transport by using the vector transport of type `T` in the embedding and projecting the result.

# Constructor

```
EmbeddedVectorTransport(vt::AbstractVectorTransportMethod)
```

Generate the vector transport with vector transport `vt` to use in the embedding.
