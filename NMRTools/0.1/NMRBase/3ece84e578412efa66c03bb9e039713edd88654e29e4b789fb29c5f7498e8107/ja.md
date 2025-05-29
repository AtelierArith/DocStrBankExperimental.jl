```
coherenceorder(coherence)
```

合計コヒーレンスオーダーを計算します。

# 例

```jldoctest
julia> coherenceorder(SQ(H1))
1

julia> coherenceorder(MQ(((H1,1),(C13,1))))
2

julia> coherenceorder(MQ(((H1,1),(C13,-1))))
0

julia> coherenceorder(MQ(((H1,3),(C13,1))))
4

julia> coherenceorder(MQ(((H1,0),)))
0
```

参照してください [`Nucleus`](@ref), [`SQ`](@ref), [`MQ`](@ref).
