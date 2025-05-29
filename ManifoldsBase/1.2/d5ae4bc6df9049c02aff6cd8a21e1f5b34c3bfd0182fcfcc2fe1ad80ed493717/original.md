```
VectorTransportWithKeywords{V<:AbstractVectorTransportMethod, K} <: AbstractVectorTransportMethod
```

Since vector transports might have keywords, this type is a way to set them as an own type to be used as a specific vector transport. Another reason for this type is that we dispatch on the vector transport first and only the last layer would be implemented with keywords, so this way they can be passed down.

## Fields

  * `vector_transport` the vector transport that is decorated with keywords
  * `kwargs` the keyword arguments

Note that you can nest this type. Then the most outer specification of a keyword is used.

## Constructor

```
VectorTransportWithKeywords(m::T; kwargs...) where {T <: AbstractVectorTransportMethod}
```

Specify the subtype `T <:`[`AbstractVectorTransportMethod`](@ref) to have keywords `kwargs...`.
