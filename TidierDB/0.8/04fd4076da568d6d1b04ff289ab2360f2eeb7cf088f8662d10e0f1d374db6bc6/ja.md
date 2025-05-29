```
  @separate(sql_query, from_col, into_cols, sep)
```

指定された区切り文字に基づいて文字列列を複数の新しい列に分割します。

# 引数

  * `sql_query`: SQLクエリ
  * `from_col`: 分割される列
  * `into_cols`: 新しい列名、[]または()をサポート
  * `sep`: 分割に使用する文字列または文字

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(a = ["1-1", "2-2", "3-3-3"]); 

julia> @chain dt(db, df, "df") @separate(a, [b, c, d], "-") @collect
3×3 DataFrame
 Row │ b       c       d       
     │ String  String  String? 
─────┼─────────────────────────
   1 │ 1       1       missing 
   2 │ 2       2       missing 
   3 │ 3       3       3

julia> @chain dt(db, df, "df") @separate( a, [c, d], "-") @collect
3×2 DataFrame
 Row │ c       d      
     │ String  String 
─────┼────────────────
   1 │ 1       1
   2 │ 2       2
   3 │ 3       3-3
```
