```
BareInterval{T<:NumTypes}
```

Interval type for guaranteed computation with interval arithmetic according to the IEEE Standard 1788-2015. Unlike [`Interval`](@ref), this bare interval does not have decorations, is not a subtype of `Real` and errors on operations mixing `BareInterval` and `Number`.

Fields:

  * `lo :: T`
  * `hi :: T`

Constructor compliant with the IEEE Standard 1788-2015: [`bareinterval`](@ref).

See also: [`Interval`](@ref).
