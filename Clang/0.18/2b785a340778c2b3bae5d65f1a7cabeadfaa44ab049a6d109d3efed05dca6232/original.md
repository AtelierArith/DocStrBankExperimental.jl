```
spelling(t::Union{CXType,CLType}) -> String
```

Pretty-print the underlying type using the rules of the language of the translation unit from which it came. If the type is invalid, an empty string is returned. Wrapper for libclang's [`clang_getTypeSpelling`](@ref).
