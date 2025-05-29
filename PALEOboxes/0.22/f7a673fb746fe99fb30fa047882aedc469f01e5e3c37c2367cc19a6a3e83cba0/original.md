```
Attribute{T}
```

Definition for Variable attribute `name`. Defines a data type `T`, a `default_value`, `required` (`true` if always present ie added with `default_value` when Variable is created), `units`, and an optional `description`.

Note that Variable attributes are stored as a per-Variable `Dict(name => value)`, these definitions are only used to provide defaults, check types, and provide descriptive metadata.

`ParseFromString` should usually be `Nothing`: a value of `Type T` is then required when calling [`set_attribute!`](@ref). If `ParseFromString` is `true`, then [`set_attribute!`](@ref) will accept an `AbstractString` and call `Base.parse(T, strvalue)` to convert to `T`. This allows eg an enum-valued Attribute to be defined by Attribute{EnumType, true} and implementing parse(EnumType, rawvalue::AbstractString)
