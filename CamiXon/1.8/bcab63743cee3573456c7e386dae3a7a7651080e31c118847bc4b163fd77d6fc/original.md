```
Value(val::Real, unit::String)
```

Object to hold a real numerical value together with a unit specifier.

The fields are:

  * `.val`: numerical value (`::Real`)
  * `.unit`: unit specifier (`::String`)

#### Example:

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> f.val
1

julia> f.unit
"Hz"
```
