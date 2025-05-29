```
uparse(string [; unit_context=ctx])
```

Parse a string as a unit or quantity. The format for `string` must be a valid Julia expression, and any identifiers will be looked up in the context `ctx`, which may be a `Module` or a vector of `Module`s. By default `unit_context=Unitful`.

Examples:

```jldoctest
julia> uparse("m/s")
m s^-1

julia> uparse("1.0*dB")
1.0 dB
```
