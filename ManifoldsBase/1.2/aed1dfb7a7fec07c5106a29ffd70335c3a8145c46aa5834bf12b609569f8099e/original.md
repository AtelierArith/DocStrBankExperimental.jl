```
RetractionWithKeywords{R<:AbstractRetractionMethod,K} <: AbstractRetractionMethod
```

Since retractions might have keywords, this type is a way to set them as an own type to be used as a specific retraction. Another reason for this type is that we dispatch on the retraction first and only the last layer would be implemented with keywords, so this way they can be passed down.

## Fields

  * `retraction` the retraction that is decorated with keywords
  * `kwargs` the keyword arguments

Note that you can nest this type. Then the most outer specification of a keyword is used.

## Constructor

```
RetractionWithKeywords(m::T; kwargs...) where {T <: AbstractRetractionMethod}
```

Specify the subtype `T <:`[`AbstractRetractionMethod`](@ref) to have keywords `kwargs...`.
