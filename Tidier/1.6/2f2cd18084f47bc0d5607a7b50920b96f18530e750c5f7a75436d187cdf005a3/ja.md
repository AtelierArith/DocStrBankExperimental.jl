```
@arrange(df, exprs...)
```

指定された列の値によってDataFrameの行を並べ替えます。

# 引数

  * `df`: DataFrame。
  * `exprs...`: 入力DataFrameからの変数。降順に並べ替えるには`desc()`を使用します。複数の変数を指定することができ、カンマで区切ります。

# 例

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = 1:10, c = 11:20);
  
julia> @chain df begin
         @arrange(a)
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         1     11
   2 │ a         2     12
   3 │ b         3     13
   4 │ b         4     14
   5 │ c         5     15
   6 │ c         6     16
   7 │ d         7     17
   8 │ d         8     18
   9 │ e         9     19
  10 │ e        10     20

julia> @chain df begin
         @arrange(a, desc(b))
       end
10×3 DataFrame
 Row │ a     b      c     
     │ Char  Int64  Int64 
─────┼────────────────────
   1 │ a         2     12
   2 │ a         1     11
   3 │ b         4     14
   4 │ b         3     13
   5 │ c         6     16
   6 │ c         5     15
   7 │ d         8     18
   8 │ d         7     17
   9 │ e        10     20
  10 │ e         9     19
```

```
@arrange(sql_query, columns...)
```

指定された列に基づいてSQLテーブルの行を並べ替えます。注意すべきは、`@arrange`は順序付きウィンドウ関数を実行する際には使用すべきではなく、`@window_order`、または好ましくは`@mutate`の`_order`引数を使用すべきです。

# 引数

  * `sql_query::SQLQuery`: 並べ替えるSQLクエリ
  * `columns`: 行を並べ替えるための列。ネストされたソートのために複数の列を含めることができます。降順にするには列名を`desc()`で囲みます。

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
