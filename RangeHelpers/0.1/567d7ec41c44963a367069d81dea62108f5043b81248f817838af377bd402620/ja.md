```
prolong(r::AbstractRange;start=nothing, stop=nothing, pre=nothing, post=nothing)
```

既存の範囲 `r` を引数に従って延長します：

```jldoctest
julia> using RangeHelpers

julia> r = 1.0:0.5:3.0
1.0:0.5:3.0

julia> prolong(r, stop=around(4))
1.0:0.5:4.0

julia> prolong(r, pre=1)
0.5:0.5:3.0

julia> prolong(r, pre=1, post=2)
0.5:0.5:4.0

julia> prolong(r, start=below(0.4), stop=around(4.1))
0.0:0.5:4.0
```
