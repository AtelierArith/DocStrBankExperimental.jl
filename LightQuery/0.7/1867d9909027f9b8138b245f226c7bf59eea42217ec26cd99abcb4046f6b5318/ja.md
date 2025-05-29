```
Group(ungrouped::By)
```

`ungrouped`内の連続したアイテムをグループ化します。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred collect(Group(By([1, -1, -2, 2, 3, -3], abs)))
3-element Array{Tuple{Int64,SubArray{Int64,1,Array{Int64,1},Tuple{UnitRange{Int64}},true}},1}:
 (1, [1, -1])
 (2, [-2, 2])
 (3, [3, -3])

julia> (@inferred collect(Group(By(Int[], abs)))) == []
true
```

事前にソートされたオブジェクトが必要です（[`By`](@ref)を参照）；そうでない場合は[`order`](@ref)を最初に実行してください。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> first_group = @> [2, 1, 2, 1] |> order(_, identity) |> Group(By(_, identity)) |> first;


julia> key(first_group)
1

julia> collect(value(first_group))
2-element Array{Int64,1}:
 1
 1
```
