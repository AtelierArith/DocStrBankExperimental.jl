```
asqtype(x::T) where {T<:Unitful.Units} -> Type
```

A helper function to convert from the "dimensions" of a Unitful quantity to the "quantities", as they are treated separately.
