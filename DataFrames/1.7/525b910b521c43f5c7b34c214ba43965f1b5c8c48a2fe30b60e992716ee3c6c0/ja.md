```
proprow
```

各グループに属する行の割合、すなわちその行数を `GroupedDataFrame` の総行数で割った値を計算します。

この関数は、`GroupedDataFrame` を変換関数（[`combine`](@ref), [`select`](@ref) など）に渡す際に、`proprow => target_col_name` 構文（またはターゲット列名を指定せずに単に `proprow`）を介してのみ使用できます。

# 例

```jldoctest
julia> df = DataFrame(id=["a", "c", "b", "b", "a", "b"])
6×1 DataFrame
 Row │ id
     │ String
─────┼────────
   1 │ a
   2 │ c
   3 │ b
   4 │ b
   5 │ a
   6 │ b

julia> gdf = groupby(df, :id);

julia> combine(gdf, proprow)
3×2 DataFrame
 Row │ id      proprow
     │ String  Float64
─────┼──────────────────
   1 │ a       0.333333
   2 │ c       0.166667
   3 │ b       0.5

julia> select(gdf, proprow => :frac)
6×2 DataFrame
 Row │ id      frac
     │ String  Float64
─────┼──────────────────
   1 │ a       0.333333
   2 │ c       0.166667
   3 │ b       0.5
   4 │ b       0.5
   5 │ a       0.333333
   6 │ b       0.5
```
