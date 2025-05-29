```
getCanonicalType(t::CXType) -> CXType
getCanonicalType(t::CLType) -> CLType
```

Return the canonical type for a CXType.

Clang's type system explicitly models typedefs and all the ways a specific type can be represented. The canonical type is the underlying type with all the "sugar" removed. For example, if 'T' is a typedef for 'int', the canonical type for 'T' would be 'int'. Wrapper for libclang's [`clang_getCanonicalType`](@ref).
