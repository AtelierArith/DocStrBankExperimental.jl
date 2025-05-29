```
  @unite(sql_query, new_cols, from_cols, sep, remove = true)
```

特定の区切り文字を使用して複数の列を1つの新しい列に分割します

# 引数

  * `sql_query`: SQLクエリ
  * `new_col`: 組み合わせを受け取る新しい列
  * `from_cols`: 組み合わせる列名、[]または()をサポート
  * `sep`: 新しい列の値を区切る文字列または文字

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame( b = ["1", "2", "3"], c = ["1", "2", "3"], d = [missing, missing, "3"]);

julia> @chain dt(db, df, "df") @unite(new_col, (b, c, d), "-") @collect
3×1 DataFrame
 Row │ new_col 
     │ String  
─────┼─────────
   1 │ 1-1
   2 │ 2-2
   3 │ 3-3-3
```
