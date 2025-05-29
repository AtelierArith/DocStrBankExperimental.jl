```
   @window_order(sql_query, columns...)
```

SQLクエリ内のウィンドウ関数の行の順序を指定します。

# 引数

  * `sql_query`: 操作するSQLクエリ。
  * `columns`: ウィンドウ関数の行を並べ替えるための列。ネストされたソートのために複数の列を含めることができます。降順にするには、列名の前に - を付けます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
        @group_by groups
        @window_frame(3)
        @window_order(desc(percent))
        @mutate(avg = mean(value))
       #@show_query 
       end;
```
