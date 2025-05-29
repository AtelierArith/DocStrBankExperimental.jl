```
@slice_min(df, column; with_ties = true, n, prop, missing_rm = true)
```

指定された列の最小値を持つ行をDataFrameまたはGroupedDataFrameから取得します。

# 引数

  * `df`: 行をスライスする元のデータフレームまたはグループ化されたデータフレーム。
  * `column`: 最小値をスライスするための列。
  * `with_ties`: すべてのタイを表示するかどうか、デフォルトはtrueで、すべてのタイを表示します。falseの場合は最初の行のみを表示します。
  * `prop`: スライスする行の割合。
  * `n`: 取得する最小行の数を指定するオプションの整数引数。with_ties = trueの場合、タイがnを超えるとnは上書きされます。
  * `missing_rm`: デフォルトはtrueで、データフレームのスライス割合を決定する際に欠損値をスキップします。

# 例

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 0.3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_min(b)
       end 
2×3 DataFrame
 Row │ a         b         c         
     │ Float64?  Float64?  Float64?  
─────┼───────────────────────────────
   1 │  missing       0.3        0.2
   2 │  missing       0.3  missing

julia> @chain df begin
         @slice_min(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │  missing       0.3       0.2

julia> @chain df begin
         @slice_min(b, n = 3)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2  
   
julia> @chain df begin
         @slice_min(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a          b         c         
     │ Float64?   Float64?  Float64?  
─────┼────────────────────────────────
   1 │ missing         0.3        0.2
   2 │ missing         0.3  missing   
   3 │       0.2       2.0        0.2
```

```
@slice_min(sql_query, column, n = 1)
```

指定された列の最小値を持つ行を選択します。これは常にタイを返します。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `column`: 最小値を特定するための列。
  * `n`: 各指定された列の最小値を持つ行の数。デフォルトは1で、最小値を持つ行を選択します。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_min(value, n = 2)
         @arrange(groups, percent) # arranged due to duckdb multi threading
         @collect
       end
4×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         2
   2 │ AF      aa          1      0.6         1
   3 │ AA      bb          1      0.1         1
   4 │ AG      bb          2      0.7         2

julia> @chain dt(db, df, "df_view") begin
         @slice_min(value)
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AA      bb          1      0.1         1
   2 │ AF      aa          1      0.6         1

julia> @chain dt(db, df, "df_view") begin
         @filter(percent > .1)
         @slice_min(percent)
         @collect
       end
1×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         1

julia> @chain dt(db, df, "df_view") begin
         @group_by groups
         @slice_min(percent)
         @arrange groups
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AB      aa          2      0.2         1
   2 │ AA      bb          1      0.1         1

julia> @chain dt(db, df, "df_view") begin
         @summarize(percent_mean = mean(percent), _by = groups)
         @slice_min(percent_mean)
         @collect
       end
1×3 DataFrame
 Row │ groups  percent_mean  rank_col 
     │ String  Float64       Int64    
─────┼────────────────────────────────
   1 │ bb               0.5         1
```
