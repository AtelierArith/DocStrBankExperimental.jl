```
@drop_missing(sql_query, [cols...])
```

欠損値のあるすべての行を削除します。

引数なしで呼び出すと、`@drop_missing()`は任意の列に欠損値があるすべての行を削除します。列がオプションの引数として提供されると、行を削除する際には指定された列の欠損値のみが考慮されます。

# 引数

  * `sql_query`: SQLクエリ
  * `cols...`: オプションの列、またはカンマで区切られた複数の列、または選択ヘルパーを使用して指定された列。

# 例

```jldoctest
julia> df = DataFrame(
              a = [1, 2, missing, 4],
              b = [1, missing, 3, 4]
            )
4×2 DataFrame
 Row │ a        b       
     │ Int64?   Int64?  
─────┼──────────────────
   1 │       1        1
   2 │       2  missing 
   3 │ missing        3
   4 │       4        4

julia> db = connect(duckdb()); dbdf = dt(db, df, "df");

julia> @chain dbdf @drop_missing() @collect
2×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      1
   2 │     4      4

julia> @chain dbdf @drop_missing(a) @collect
3×2 DataFrame
 Row │ a      b       
     │ Int64  Int64?  
─────┼────────────────
   1 │     1        1
   2 │     2  missing 
   3 │     4        4

julia> @chain dbdf @drop_missing(a, b) @collect
2×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      1
   2 │     4      4

julia> @chain dbdf @drop_missing(starts_with("a")) @collect
3×2 DataFrame
 Row │ a      b       
     │ Int64  Int64?  
─────┼────────────────
   1 │     1        1
   2 │     2  missing 
   3 │     4        4
```
