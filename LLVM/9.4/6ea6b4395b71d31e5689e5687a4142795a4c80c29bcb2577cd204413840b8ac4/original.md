```
convert(::Type{<:AbstractFloat}, val::GenericValue, typ::LLVM.FloatingPointType)
```

Convert a generic value to a floating point number of the given type.

Contrary to the integer conversion, the LLVM type is also required to be passed explicitly.
