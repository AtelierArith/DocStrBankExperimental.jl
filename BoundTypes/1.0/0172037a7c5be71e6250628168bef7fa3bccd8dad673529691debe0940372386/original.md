```
bound_value(x) -> value
```

Getter function for the underlying value from the bound type object `x`.

## Examples

```jldoctest
julia> val = StringFixedLength{String,3}("abc")
"abc"

julia> typeof(val)
StringFixedLength{String, 3}

julia> inner_val = bound_value(val)
"abc"

julia> typeof(inner_val)
String
```
