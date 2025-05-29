```
@count(sql_query, columns...)
```

指定された列でグループ化された行の数をカウントします。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `columns`: カウントする前にグループ化する列。列が指定されていない場合、クエリ内のすべての行をカウントします。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @count(groups)
         @arrange(groups)
         @collect
       end
2×2 DataFrame
 Row │ groups  n     
     │ String  Int64 
─────┼───────────────
   1 │ aa          5
   2 │ bb          5
```
