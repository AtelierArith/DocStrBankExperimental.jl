```
static"string"[N]
```

Create a [`StaticString`](@ref) from "string". Optionally, specify the number of codeunits, `N`.

# Examples

```jldoctest
julia> static"großartig"
static"großartig"10

julia> static"verehrungswürdig"20
static"verehrungswürdig\0\0\0"20
```
