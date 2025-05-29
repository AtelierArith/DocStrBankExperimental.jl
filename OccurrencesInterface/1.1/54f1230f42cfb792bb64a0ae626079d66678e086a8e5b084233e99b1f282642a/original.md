```
presences(c::T) where {T<:AbstractOccurrenceCollection}
```

Returns an `Occurrences` where only the occurrences in the initial collection for which `presence` evaluates to `true` are kept.
