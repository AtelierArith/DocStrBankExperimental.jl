```
@union(sql_query1, sql_query2)
```

2つのSQLクエリを`UNION ALL`演算子を使用して結合します。

# 引数

  * `sql_query1`: 結合する最初のSQLクエリ。
  * `sql_query2`: 結合する2番目のSQLクエリ。

# 戻り値

  * 最初のクエリにバインドされた2番目のクエリのすべての行の遅延クエリ

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df1 = DataFrame(id = [1, 2, 3], value = [10, 20, 30]);

julia> df1_table = dt(db, df1, "df1");

julia> @chain df1_table @union_all(df1_table) @collect
6×2 DataFrame
 Row │ id     value 
     │ Int64  Int64 
─────┼──────────────
   1 │     1     10
   2 │     2     20
   3 │     3     30
   4 │     1     10
   5 │     2     20
   6 │     3     30
```
