```
groupindices(gd::GroupedDataFrame)
```

`parent(gd)`の各行に対するグループインデックスのベクターを返します。

グループ`gd[i]`に現れる行はインデックス`i`が割り当てられます。どのグループにも存在しない行には`missing`が割り当てられます（これは、`gd`を作成する際に`skipmissing=true`が渡された場合や、`gd`がより大きな[`GroupedDataFrame`](@ref)のサブセットである場合に発生する可能性があります）。

`groupindices => target_col_name`構文（またはターゲット列名を指定せずに単に`groupindices`）は、`GroupedDataFrame`を変換関数（[`combine`](@ref)、[`select`](@ref)など）に渡す際の変換ミニ言語でもサポートされています。

# 例

```jldoctest
julia> df = DataFrame(id=["a", "c", "b", "b", "a"])
5×1 DataFrame
 Row │ id
     │ String
─────┼────────
   1 │ a
   2 │ c
   3 │ b
   4 │ b
   5 │ a

julia> gdf = groupby(df, :id);

julia> combine(gdf, groupindices)
3×2 DataFrame
 Row │ id      groupindices
     │ String  Int64
─────┼──────────────────────
   1 │ a                  1
   2 │ c                  2
   3 │ b                  3

julia> select(gdf, groupindices => :gid)
5×2 DataFrame
 Row │ id      gid
     │ String  Int64
─────┼───────────────
   1 │ a           1
   2 │ c           2
   3 │ b           3
   4 │ b           3
   5 │ a           1
```
