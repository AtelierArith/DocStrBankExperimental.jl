```
SplitAxis(ax::AbstractUnitRange, n::Real)
```

`ax`を`ceil(Int, n)`個のほぼ同じサイズのチャンクに分割します。最初のチャンクは他のチャンクより大きくならず、`n`の小数部分の「不足」は最初のチャンクをさらに小さくします。

これは、スレッド間で作業を分割するのに役立ちます。最初のスレッドが他のスレッドに作業を割り当てる責任を負っている場合、スケジューリングにかかる時間を考慮して、少ない作業を割り当てることがしばしば有用です。

# 例

```jldoctest; setup=:(using TiledIteration)
julia> collect(SplitAxis(1:16, 4))
4-element Vector{UnitRange{Int64}}:
 1:4
 5:8
 9:12
 13:16

julia> collect(SplitAxis(1:16, 3.5))
4-element Vector{UnitRange{Int64}}:
 1:1
 2:6
 7:11
 12:16
```

後者の場合、最初のチャンクを除くすべての範囲の長さは5であるため、最初のチャンクには1つの要素しか残りません。
