```
Rows(named_columns)
```

テーブルの `rows` に対するイテレータ。常に遅延評価。表示するには [`Peek`](@ref) を使用します。

```jldoctest Rows
julia> using LightQuery


julia> using Test: @inferred


julia> lazy = @inferred Rows(a = [1, 2], b = [1.0, 2.0])
2-element Rows{NamedTuple{(:a, :b),Tuple{Int64,Float64}},1,Tuple{Array{Int64,1},Array{Float64,1}},Tuple{Name{:a},Name{:b}}}:
 (a = 1, b = 1.0)
 (a = 2, b = 2.0)

julia> @inferred collect(lazy)
2-element Array{NamedTuple{(:a, :b),Tuple{Int64,Float64}},1}:
 (a = 1, b = 1.0)
 (a = 2, b = 2.0)

julia> @inferred Rows(a = [1, 2])
2-element Rows{NamedTuple{(:a,),Tuple{Int64}},1,Tuple{Array{Int64,1}},Tuple{Name{:a}}}:
 (a = 1,)
 (a = 2,)
```

Rows へのすべての引数は同じ軸を持っている必要があります。チェックをオーバーライドするには `@inbounds` を使用します。

```jldoctest Rows
julia> result = Rows(a = 1:2, b = 1:3)
ERROR: DimensionMismatch("All columns passed to `Rows` must have the same axes")
[...]
```
