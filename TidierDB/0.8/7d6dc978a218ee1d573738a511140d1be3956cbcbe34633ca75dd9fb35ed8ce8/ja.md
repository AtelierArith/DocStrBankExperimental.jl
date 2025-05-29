```
@head(sql_query, value)
```

指定された値に基づいて返されるSQLテーブルの行数を制限します。 `LIMIT` in SQL

# 引数

  * `sql_query`: 操作するSQLクエリ。
  * `value`: 返される行数を制限するための数値。空のままにすると、デフォルトで6行になります。

# 例

```jldoctest
julia> db = connect(duckdb());

julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);
                     

julia> @chain dt(db, df, "df_view") begin
        @head(1) ## 式をサポートします。つまり、`3-2`は以下の同じdfを返します
        @collect
       end
1×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AA      bb          1      0.1
```
