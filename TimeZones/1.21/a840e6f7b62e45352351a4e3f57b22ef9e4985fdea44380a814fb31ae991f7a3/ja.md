```
FixedTimeZone(::AbstractString) -> FixedTimeZone
```

文字列からUTCオフセットを持つ`FixedTimeZone`を構築します。結果として得られる`FixedTimeZone`は「UTC±HH:MM[:SS]」のように名付けられます。

# 例

```julia
julia> FixedTimeZone("UTC+6")
UTC+06:00

julia> FixedTimeZone("-1330")
UTC-13:30

julia> FixedTimeZone("15:45:21")
UTC+15:45:21
```
