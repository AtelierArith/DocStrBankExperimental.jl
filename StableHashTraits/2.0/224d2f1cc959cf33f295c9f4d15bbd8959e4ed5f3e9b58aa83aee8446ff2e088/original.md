```
WithTypeNames(parent_context)
```

In this hash context, [`StableHashTraits.transform_type`](@ref) returns [`module_nameof_string`](@ref) for all types, in contrast to the default behavior (which mostly uses `nameof_string(StructType(T))`).

!!! warn "Unstable"
    `module_nameof_string`'s return value can change with non-breaking changes if e.g. the module of a function or type is changed because it's considered an implementation detail of a package.

