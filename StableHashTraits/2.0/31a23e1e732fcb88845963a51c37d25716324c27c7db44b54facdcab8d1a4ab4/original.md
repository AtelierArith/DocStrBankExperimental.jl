```
nameof_string(::Type{T})
nameof_string(T::Module)
nameof_string(::T) where {T}
```

Get a stable name of `T`. This is a helpful utility for writing your own methods of [`StableHashTraits.transform_type`](@ref) and [`StableHashTraits.transform_type_value`](@ref). The stable name is computed from `nameof`. Anonymous names (e.g. `module_nameof_string(x -> x+1)`) throw an error, as no stable name is possible in this case.
