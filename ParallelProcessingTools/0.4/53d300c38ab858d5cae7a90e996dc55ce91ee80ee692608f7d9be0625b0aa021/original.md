```
abstract type WriteMode
```

Abstract type for write modes.

May be one of the following subtypes: [`CreateNew`](@ref), [`CreateOrIgnore`](@ref), [`CreateOrReplace`](@ref), [`CreateOrModify`](@ref), [`ModifyExisting`](@ref).

Used by [`write_files`](@ref).
