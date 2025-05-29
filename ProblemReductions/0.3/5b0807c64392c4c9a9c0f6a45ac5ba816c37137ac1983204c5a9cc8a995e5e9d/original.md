```
onehotv(::Type{<:StaticElementVector}, i, v)
onehotv(::Type{<:StaticBitVector}, i)
```

Returns a static element vector, with the value at location `i` being `v` (1 if not specified).
