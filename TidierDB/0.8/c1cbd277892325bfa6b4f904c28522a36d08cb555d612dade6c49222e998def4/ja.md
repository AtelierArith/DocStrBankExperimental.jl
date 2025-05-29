```
@mutate(sql_query, exprs...; _by, _frame, _order)
```

SQLテーブルを新しい列を追加したり、既存の列を修正することで変更します。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `exprs`: テーブルを変更するための式。新しい列を追加したり、既存の列を`column_name = expression syntax`を使用して修正できます。ここで、expressionは既存の列を含むことができます。
  * `_by`: マクロ呼び出しでの変換のためにグループ化を可能にする単一の列名または列のベクターをサポートするオプションの引数
  * `_frame`: `@mutate`内でウィンドウフレームを決定することを可能にするオプションの引数。単一の数字または数字のタプルをサポートします。`desc()`プレフィックスをサポートします
  * `_order`: `@mutate`内でウィンドウの順序を決定することを可能にするオプションの引数。単一の列または名前のベクターをサポートします

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @mutate(value = value * 4, new_col = percent^2)
         @collect
       end
10×5 DataFrame
 Row │ id      groups  value  percent  new_col 
     │ String  String  Int64  Float64  Float64 
─────┼─────────────────────────────────────────
   1 │ AA      bb          4      0.1     0.01
   2 │ AB      aa          8      0.2     0.04
   3 │ AC      bb         12      0.3     0.09
   4 │ AD      aa         16      0.4     0.16
   5 │ AE      bb         20      0.5     0.25
   6 │ AF      aa          4      0.6     0.36
   7 │ AG      bb          8      0.7     0.49
   8 │ AH      aa         12      0.8     0.64
   9 │ AI      bb         16      0.9     0.81
  10 │ AJ      aa         20      1.0     1.0

julia> @chain dt(db, df, "df_view") begin
         @mutate(max = maximum(percent), sum = sum(percent), _by = groups)
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  max      sum     
     │ String  String  Int64  Float64  Float64  Float64 
─────┼──────────────────────────────────────────────────
   1 │ AB      aa          2      0.2      1.0      3.0
   2 │ AD      aa          4      0.4      1.0      3.0
   3 │ AF      aa          1      0.6      1.0      3.0
   4 │ AH      aa          3      0.8      1.0      3.0
   5 │ AJ      aa          5      1.0      1.0      3.0
   6 │ AA      bb          1      0.1      0.9      2.5
   7 │ AC      bb          3      0.3      0.9      2.5
   8 │ AE      bb          5      0.5      0.9      2.5
   9 │ AG      bb          2      0.7      0.9      2.5
  10 │ AI      bb          4      0.9      0.9      2.5

julia> @chain dt(db, df, "df_view") begin
          @mutate(value1 = sum(value), 
                      _order = percent, 
                      _frame = (-1, 1), 
                      _by = groups) 
          @mutate(value2 = sum(value), 
                      _order = desc(percent),
                      _frame = 2)  
          @arrange(groups)
          @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  value1  value2  
     │ String  String  Int64  Float64  Int128  Int128? 
─────┼─────────────────────────────────────────────────
   1 │ AJ      aa          5      1.0       8       21
   2 │ AH      aa          3      0.8       9       16
   3 │ AF      aa          1      0.6       8       10
   4 │ AD      aa          4      0.4       7        3
   5 │ AB      aa          2      0.2       6  missing 
   6 │ AI      bb          4      0.9       6       18
   7 │ AG      bb          2      0.7      11       15
   8 │ AE      bb          5      0.5      10        6
   9 │ AC      bb          3      0.3       9        1
  10 │ AA      bb          1      0.1       4  missing 

julia> @chain dt(db, df, "df_view") begin
         @mutate(across([:value, :percent], agg(kurtosis)))
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  value_kurtosis  percent_kurtosis 
     │ String  String  Int64  Float64  Float64         Float64          
─────┼──────────────────────────────────────────────────────────────────
   1 │ AA      bb          1      0.1        -1.33393              -1.2
   2 │ AB      aa          2      0.2        -1.33393              -1.2
   3 │ AC      bb          3      0.3        -1.33393              -1.2
   4 │ AD      aa          4      0.4        -1.33393              -1.2
   5 │ AE      bb          5      0.5        -1.33393              -1.2
   6 │ AF      aa          1      0.6        -1.33393              -1.2
   7 │ AG      bb          2      0.7        -1.33393              -1.2
   8 │ AH      aa          3      0.8        -1.33393              -1.2
   9 │ AI      bb          4      0.9        -1.33393              -1.2
  10 │ AJ      aa          5      1.0        -1.33393              -1.2

julia> @chain dt(db, df, "df_view") begin
          @mutate(value2 = sum(value), 
                      _order = desc([:value, :percent]),
                      _frame = 2);  
          @collect
       end;
```
