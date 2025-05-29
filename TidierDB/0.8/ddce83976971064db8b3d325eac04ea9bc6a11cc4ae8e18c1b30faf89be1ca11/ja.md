```
@setdiff(sql_query1, sql_query2, all = false)
```

2つのSQLクエリ/テーブルを`EXCEPT`を使用して結合します

# 引数

  * `sql_query1`: 結合する最初のSQLクエリ。
  * `sql_query2`: 結合する2番目のSQLクエリ。
  * `all`: デフォルトはfalseで、trueの場合は重複を返します。`EXCEPT ALL`

# 戻り値

  * 最初のクエリにバインドされた2番目のクエリのすべての行の遅延クエリ

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df1 = DataFrame(id = [1, 1, 2, 2, 3, 4],
        name = ["Alice", "Alice", "Bob", "Bob", "Charlie", "David"]);

julia> df2 = DataFrame(id = [2, 2, 3, 5],
       name = ["Bob", "Bob", "Charlie", "Eve"]);

julia> df1_table = dt(db, df1, "df1"); 

julia> df2_table = dt(db, df2, "df2");

julia> @chain df1_table @setdiff(df2_table) @collect
2×2 DataFrame
 Row │ id     name   
     │ Int64  String 
─────┼───────────────
   1 │     1  Alice
   2 │     4  David

julia> @chain df1_table @setdiff(df2_table, all = true) @collect
3×2 DataFrame
 Row │ id     name   
     │ Int64  String 
─────┼───────────────
   1 │     1  Alice
   2 │     1  Alice
   3 │     4  David
```
