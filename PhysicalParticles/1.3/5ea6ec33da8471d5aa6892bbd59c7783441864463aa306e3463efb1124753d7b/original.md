```
axisunit(::Nothing)
axisunit(u::Units)
axisunit(s::AbstractString, u::Units)
```

Return a String for pretty printing.

# Examples

```jl
julia> axisunit(nothing)
""

julia> axisunit(u"m")
" [m]"

julia> axisunit("Time", u"Gyr")
"Time [Gyr]"
```
