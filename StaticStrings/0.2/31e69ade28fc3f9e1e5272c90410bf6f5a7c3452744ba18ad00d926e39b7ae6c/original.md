```
CStaticString(data::NTuple{N,UInt8})
cstatic"string"N
```

[`AbstractStaticString`](@ref) that stores codeunits in a NTuple{N,UInt8} but requires NUL codeunits to be at the end.

Converting to a `String` will include null bytes. Use `strip` to get a `SubString` without the null bytes.

N.B. The size of a `CStaticString{N}` is `N+1` bytes.
