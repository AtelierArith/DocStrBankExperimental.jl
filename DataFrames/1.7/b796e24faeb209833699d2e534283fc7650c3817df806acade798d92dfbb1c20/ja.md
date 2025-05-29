```
AsTable(cols)
```

`source => transformation => destination` 選択操作において特別な意味を持つ型で、[`combine`](@ref)、[`select`](@ref)、[`select!`](@ref)、[`transform`](@ref)、[`transform!`](@ref)、[`subset`](@ref)、および [`subset!`](@ref) によってサポートされています。

`AsTable(cols)` が `source` の位置で使用されると、ラップされたセレクタ `cols` によって選択された列が `NamedTuple` として関数に渡されることを示します。

`AsTable` が `destination` の位置で使用されると、`transformation` 操作の結果がコンテナのベクター（または `ByRow(transformation)` が使用されている場合は単一のコンテナ）であり、`keys` を使用して列名を取得するために複数の列に展開されるべきことを意味します。

# 例

```jldoctest
julia> df1 = DataFrame(a=1:3, b=11:13)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13

julia> df2 = select(df1, AsTable([:a, :b]) => ByRow(identity))
3×1 DataFrame
 Row │ a_b_identity
     │ NamedTuple…
─────┼─────────────────
   1 │ (a = 1, b = 11)
   2 │ (a = 2, b = 12)
   3 │ (a = 3, b = 13)

julia> select(df2, :a_b_identity => AsTable)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13

julia> select(df1, AsTable([:a, :b]) => ByRow(nt -> map(x -> x^2, nt)) => AsTable)
3×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1    121
   2 │     4    144
   3 │     9    169
```
