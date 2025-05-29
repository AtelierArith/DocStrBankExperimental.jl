@pivot*wider(df, names*from, values_from)

SQL_queryをリシェイプして、列の数を増やし、行の数を減らします。

`@pivot_wider`は、`names_from`列の異なる値を引き出すための熱意を必要とします。これは、`@pivot_wider`のポイントまでクエリを取得し、`names_from`列の異なる値を引き出すためのクエリを実行します。

# 引数

  * `sql_query`: SQLクエリ
  * `names_from`: 出力列の名前を取得するための列の名前。
  * `values_from`: セルの値を取得するための列の名前。

# 例

```jldoctest
julia> df_long = DataFrame(id = [1, 1, 2, 2],
                           variable = ["A", "B", "A", "B"],
                           value = [1, 2, 3, 4]);

julia> db = connect(duckdb()); dbdf = dt(db, df_long, "df");

julia> @collect @pivot_wider(dbdf, names_from = variable, values_from = value)
2×3 DataFrame
 Row │ id     A      B     
     │ Int64  Int64  Int64 
─────┼─────────────────────
   1 │     1      1      2
   2 │     2      3      4

julia> future_col_names = (:variable, [:A, :B]); 

julia> @eval @collect @pivot_wider(dbdf, names_from = $future_col_names, values_from = value)
2×3 DataFrame
 Row │ id     A      B     
     │ Int64  Int64  Int64 
─────┼─────────────────────
   1 │     1      1      2
   2 │     2      3      4
```
