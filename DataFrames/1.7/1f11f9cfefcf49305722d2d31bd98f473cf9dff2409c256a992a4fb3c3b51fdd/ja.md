```
filter(fun, gdf::GroupedDataFrame; ungroup::Bool=false)
filter(cols => fun, gdf::GroupedDataFrame; ungroup::Bool=false)
```

`fun` が `true` を返す `gd` のグループのみを `GroupedDataFrame` として返します。`ungroup=false`（デフォルト）の場合、または `ungroup=true` の場合はデータフレームとして返します。

`cols` が指定されていない場合、述語 `fun` は各グループの `SubDataFrame` で呼び出されます。

`cols` が指定されている場合、述語 `fun` は対応する列のビューを別々の位置引数として各グループに対して呼び出されます。ただし、`cols` が `AsTable` セレクタの場合、これらの引数の `NamedTuple` が渡されます。`cols` は任意の列セレクタ（`Symbol`、文字列または整数; `:`, `Cols`, `All`, `Between`, `Not`、正規表現、または `Symbol`、文字列または整数のベクター）であり、`Symbol`、文字列、または整数のベクターが渡された場合は列の重複が許可されます。

!!! note
    このメソッドは、DataFrames.jl がコレクションのための Julia API を実装するように定義されていますが、一般的には他の DataFrames.jl 関数と一貫性があるため、代わりに [`subset`](@ref) 関数を使用することが推奨されます（`filter` とは対照的に）。


# 例

```jldoctest
julia> df = DataFrame(g=[1, 2], x=['a', 'b']);

julia> gd = groupby(df, :g)
GroupedDataFrame with 2 groups based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a
⋮
Last Group (1 row): g = 2
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     2  b

julia> filter(x -> x.x[1] == 'a', gd)
GroupedDataFrame with 1 group based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> filter(:x => x -> x[1] == 'a', gd)
GroupedDataFrame with 1 group based on key: g
First Group (1 row): g = 1
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a

julia> filter(:x => x -> x[1] == 'a', gd, ungroup=true)
1×2 DataFrame
 Row │ g      x
     │ Int64  Char
─────┼─────────────
   1 │     1  a
```
