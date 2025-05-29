```
samegrid(r1::AbstractRange, r2::AbstractRange; atol=0, rtol=0, kw...)::Bool
```

`r1` と `r2` が同じグリッド上に定義されているかを確認します。つまり、`r1` と `r1` の等しい延長が存在するかどうかです。

```jldoctest
julia> using RangeHelpers: samegrid

julia> samegrid(1:10, 11:12)
true

julia> samegrid(1:10, 11:1.1:12)
false

julia> samegrid(1:10, 1:0)
true

julia> samegrid(1:10, 0.1:0)
false

julia> samegrid(1:10, 5:-1:3)
true

julia> samegrid(1:10, 4.1:1:5, rtol=0.2)
true

```
