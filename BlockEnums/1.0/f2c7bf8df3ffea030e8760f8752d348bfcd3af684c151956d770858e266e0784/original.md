```
basetype(V::Type{<:BlockEnum{T}})
```

Return `T`, which is the bitstype whose values are bitcast to the type `V`. This is the type of the value returned by `Integer(x::V)`. The type is in a sense the underlying type of `V`.
