```
NamedValue(val::Value, name::String, comment::String)
```

Object to hold a [`Value`](@ref) together with its `symbolic name` and a `short` description

The fields are:

  * `.val`: Value  (`::Value`)
  * `.name`: symbolic name (`::String`)
  * `.comment`: description (`::String`)

Named Value object The object `NamedValue` is best created using [`castNamedValue`](@ref).

#### Example:

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> f = castNamedValue(f, name="frequency", comment="comment")
NamedValue(Value(1, "Hz"), "frequency", "comment")

julia> f.name
"frequency"
```
