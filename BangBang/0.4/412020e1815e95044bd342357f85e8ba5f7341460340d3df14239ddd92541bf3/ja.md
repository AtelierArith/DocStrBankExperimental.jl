```
push!!(collection, items...)
```

1つ以上の`items`をコレクションに追加します。コレクションが変更できない場合や要素の型が一致しない場合は、コレクションのコピーを作成します。

# 例

```jldoctest
julia> using BangBang

julia> push!!((1, 2), 3)
(1, 2, 3)

julia> push!!([1, 2], 3)
3-element Vector{Int64}:
 1
 2
 3

julia> push!!([1, 2], 3.0)
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> using StaticArrays: SVector

julia> @assert push!!(SVector(1, 2), 3.0) === SVector(1.0, 2.0, 3.0)

julia> using DataFrames: DataFrame

julia> @assert push!!(DataFrame(a=[1], b=[2]), (a=3.5, b=4.5)) ==
           DataFrame(a=[1.0, 3.5], b=[2.0, 4.5])

julia> using StructArrays: StructVector

julia> @assert push!!(StructVector(a=[1], b=[2]), (a=3.5, b=4.5)) ==
           StructVector(a=[1.0, 3.5], b=[2.0, 4.5])

julia> using TypedTables: Table

julia> @assert push!!(Table(a=[1], b=[2]), (a=3.5, b=4.5)) ==
           Table(a=[1.0, 3.5], b=[2.0, 4.5])
```
