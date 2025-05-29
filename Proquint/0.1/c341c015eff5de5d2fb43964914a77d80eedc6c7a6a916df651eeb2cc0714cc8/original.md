```
uint2quint(x::T, sep="-"; short=false) where T<:Integer
```

Convert an integer value into a corresponding proquint string identifier.

# Arguments

  * `x`: an integer argument,
  * `sep="-"`: a separator string,
  * `short=false`: determines whether a short string should be created.

# Example

```julia
julia> uint2quint(0x7f000001)
"lusab-babad"

julia> uint2quint(0x7f000001, short=true)
"lusab-d"
```
