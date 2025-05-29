```
spec(::Union{G, Type{G}})::GroupSpec where G <: Group
```

Constructs a specification of a group type or instance. It's general intended use is for debugging purposes and serves as an inverse to `concretize_type` method. If called with a group instance the the value of it is used for a generator for the group specification otherwise it is left empty.

See also `concretize_type`
