```
InverseRetractionWithKeywords{R<:AbstractRetractionMethod,K} <: AbstractInverseRetractionMethod
```

Since inverse retractions might have keywords, this type is a way to set them as an own type to be used as a specific inverse retraction. Another reason for this type is that we dispatch on the inverse retraction first and only the last layer would be implemented with keywords, so this way they can be passed down.

## Fields

  * `inverse_retraction` the inverse retraction that is decorated with keywords
  * `kwargs` the keyword arguments

Note that you can nest this type. Then the most outer specification of a keyword is used.

## Constructor

```
InverseRetractionWithKeywords(m::T; kwargs...) where {T <: AbstractInverseRetractionMethod}
```

Specify the subtype `T <:`[`AbstractInverseRetractionMethod`](@ref) to have keywords `kwargs...`.
