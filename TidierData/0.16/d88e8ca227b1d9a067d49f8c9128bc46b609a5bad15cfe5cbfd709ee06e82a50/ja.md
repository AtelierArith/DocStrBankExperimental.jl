@pivot*wider(df, names*from, values*from[, values*fill])

データフレームをワイドに変形し、列の数を増やし、行の数を減らします。

# 引数

  * `df`: データフレーム。
  * `names_from`: 出力列の名前を取得するための列の名前。
  * `values_from`: セルの値を取得するための列の名前。
  * `values_fill`: 欠損した名前/値の組み合わせを置き換える値（デフォルトは `missing`）

# 例

```jldoctest
julia> df_long = DataFrame(id = [1, 1, 2, 2],
                           variable = ["A", "B", "A", "B"],
                           value = [1, 2, 3, 4]);

julia> df_long_missing = DataFrame(id = [1, 1, 2],
                           variable = ["A", "B", "B"],
                           value = [1, 2, 4]);

julia> @pivot_wider(df_long, names_from = variable, values_from = value)
2×3 DataFrame
 Row │ id     A       B      
     │ Int64  Int64?  Int64?
─────┼───────────────────────
   1 │     1       1       2
   2 │     2       3       4

julia> @pivot_wider(df_long, names_from = "variable", values_from = "value")
2×3 DataFrame
 Row │ id     A       B      
     │ Int64  Int64?  Int64?
─────┼───────────────────────
   1 │     1       1       2
   2 │     2       3       4

julia> @pivot_wider(df_long_missing, names_from = variable, values_from = value, values_fill = 0)
2×3 DataFrame
 Row │ id     A      B     
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      1      2
   2 │     2      0      4
```
