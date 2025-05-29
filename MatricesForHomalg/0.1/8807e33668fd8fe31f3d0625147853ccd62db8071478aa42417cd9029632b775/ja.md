```
RingName(ring)
```

リングの名前を文字列として返します。

```jldoctest
julia> ring = HomalgRingOfIntegers()
整数リング

julia> RingName(ring)
"Z"

julia> field = HomalgFieldOfRationals()
有理数体

julia> RingName(field)
"Q"
```
