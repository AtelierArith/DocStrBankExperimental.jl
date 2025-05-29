```
tensoralloc(ttype, structure, [istemp=false, allocator])
```

Allocate memory for a tensor of type `ttype` and structure `structure`. The optional third argument can be used to indicate that the result is used as a temporary tensor, for which in some cases and with some allocators (the optional fourth argument) a different allocation strategy might be used.

See also [`tensoralloc_add`](@ref), [`tensoralloc_contract`](@ref) and [`tensorfree!`](@ref).
