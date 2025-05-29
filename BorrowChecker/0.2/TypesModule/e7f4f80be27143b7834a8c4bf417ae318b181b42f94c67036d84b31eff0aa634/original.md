```
LazyAccessor{T,P,S,O<:Union{AbstractOwned,AbstractBorrowed}} <: AbstractWrapper{T}
```

A lazy accessor for properties or indices of owned or borrowed values. Maintains ownership semantics while allowing property/index access without copying or moving.

Created automatically when accessing properties or indices of owned/borrowed values:

```julia
@own x = (a=1, b=2)
x.a  # Returns a LazyAccessor
```

# Internal fields (not part of public API):

  * `parent::P`: The parent value being accessed
  * `property::S`: The property/index being accessed
  * `property_type::Type{T}`: Type of the accessed property/index
  * `target::O`: The original owned/borrowed value
