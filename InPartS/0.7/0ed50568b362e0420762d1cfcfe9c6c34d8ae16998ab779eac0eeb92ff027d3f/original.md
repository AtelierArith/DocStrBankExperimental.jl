```
LineageRegistrar{T<:Integer} <: AbstractSeqRegistrar{T}
```

In addition to returning sequential numbers of type `T` (defaults to `UInt64`), this implementation of [`AbstractSeqRegistrar`](@ref) also can keep track of lineages using a dictionary called `parent`. Calling [`set_id!`](@ref)/[`get_id!`](@ref) on this registrar automatically records the parent as the entry `(newid -> parent_id)` in the dictionary.
