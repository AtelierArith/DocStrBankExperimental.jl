```
get_elaborated_cursor(ty::CLType) -> CLCursor
get_elaborated_cursor(ty::CXType) -> CXCursor
```

Return the cursor of the elaborated type that is referenced by the input type. The input type can be a pointer/array. This function returns [`clang_getNullCursor`](@ref) if the input type is not refer to an elaborated type.
