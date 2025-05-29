```
elements(::T) where {T<:AbstractOccurrenceCollection}
```

Returns the elements contained in an abstract collection of occurrences – this must be something that can be iterated. The default value, when unimplemented, is `nothing`. Note that when overloaded as part of your own implementation of the interface, this must return a `Vector`.
