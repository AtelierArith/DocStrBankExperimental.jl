```
convert_psd_eltype(::Type{T}, P)
```

Wraps P in a psd paramtrization of eltype T. If P is already a type of psd paramtrization, then just the eltype is converted.
