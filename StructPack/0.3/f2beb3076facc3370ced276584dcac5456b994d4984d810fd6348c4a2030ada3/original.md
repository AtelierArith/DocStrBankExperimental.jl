Abstract serialization context.

A context can be introduced to temporarily enforce custom behavior when packing and unpacking values.

In particular, a context can influence which formats are assigned to types (via [`format`](@ref)) or to fields of a struct (via [`valueformat`](@ref)). It can also influence how objects are processed before packing and after unpacking (via [`destruct`](@ref) and [`construct`](@ref)).
