```
strValue(f::Value)
```

String expression for a [`Value`](@ref) object in `:compact => true` representation

#### Example:

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> strValue(f)
"1 Hz"
```
