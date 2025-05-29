```
axisunit(::Nothing)
axisunit(u::Units)
axisunit(s::AbstractString, u::Units)
```

整形表示用の文字列を返します。

# 例

```jl
julia> axisunit(nothing)
""

julia> axisunit(u"m")
" [m]"

julia> axisunit("Time", u"Gyr")
"Time [Gyr]"
```
