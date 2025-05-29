```
@arrange(sql_query, columns...)
```

指定された列に基づいてSQLテーブルの行を並べ替えます。特に、`@arrange`は順序付きウィンドウ関数、`@window_order`を使用する場合、または好ましくは`@mutate`の`_order`引数を使用する場合には使用しないでください。

# 引数

  * `sql_query::SQLQuery`: 並べ替えるSQLクエリ
  * `columns`: 行を並べ替えるための列。ネストされたソートのために複数の列を含めることができます。降順にするには、列名を`desc()`で囲みます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @arrange(value, desc(percent))
         @collect
       end
10×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AF      aa          1      0.6
   2 │ AA      bb          1      0.1
   3 │ AG      bb          2      0.7
   4 │ AB      aa          2      0.2
   5 │ AH      aa          3      0.8
   6 │ AC      bb          3      0.3
   7 │ AI      bb          4      0.9
   8 │ AD      aa          4      0.4
   9 │ AJ      aa          5      1.0
  10 │ AE      bb          5      0.5

julia> @chain dt(db, df, "df_view") begin
         @arrange(desc(df_view.value))
         @collect
       end
10×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AE      bb          5      0.5
   2 │ AJ      aa          5      1.0
   3 │ AD      aa          4      0.4
   4 │ AI      bb          4      0.9
   5 │ AC      bb          3      0.3
   6 │ AH      aa          3      0.8
   7 │ AB      aa          2      0.2
   8 │ AG      bb          2      0.7
   9 │ AA      bb          1      0.1
  10 │ AF      aa          1      0.6
```
