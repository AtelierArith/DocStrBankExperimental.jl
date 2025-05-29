```
eltype(tele::Telegraph) → Type
```

Dispatch `Base.eltype` for the [`Telegraph`](@ref) object.

# Additional information

  * Wrapper around `Base.eltype(tele.signal)`.
