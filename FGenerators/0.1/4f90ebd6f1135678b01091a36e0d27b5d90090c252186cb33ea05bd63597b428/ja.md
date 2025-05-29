```
@yieldfrom foldable
```

`foldable` からアイテムを生成します。これは、[`@fgenerator`](@ref) マクロ内などの特別なコンテキスト内でのみ使用可能です。

## 例

```jldoctest @yieldfrom
julia> using FGenerators

julia> @fgenerator function flatten2(xs, ys)
           @yieldfrom xs
           @yieldfrom ys
       end;

julia> collect(flatten2(1:2, 11:12))
4-element Array{Int64,1}:
  1
  2
 11
 12
```
