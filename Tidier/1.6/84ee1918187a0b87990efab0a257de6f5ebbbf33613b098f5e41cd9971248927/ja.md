```
@slice_max(df, column; with_ties = true, n, prop, missing_rm = true)
```

指定された列からDataFrameまたはGroupedDataFrameの最大値を持つ行を取得します。

# 引数

  * `df`: 行をスライスする元のデータフレームまたはグループ化されたデータフレーム。
  * `column`: 最大値をスライスするための列。
  * `with_ties`: すべてのタイを表示するかどうか、デフォルトはtrue。falseの場合は最初の行のみ表示されます。
  * `prop`: スライスする行の割合。
  * `n`: 取得する最大行数を指定するオプションの整数引数。with_ties = trueの場合、タイがnを超えるとnは上書きされます。
  * `missing_rm`: デフォルトはtrue、データフレームのスライス割合を決定する際に欠損値をスキップします。

# 例

```jldoctest
julia> df = DataFrame(
           a = [missing, 0.2, missing, missing, 1, missing, 5, 6],
           b = [0.3, 2, missing, 3, 6, 5, 7, 7],
           c = [0.2, 0.2, 0.2, missing, 1, missing, 5, 6]);

julia> @chain df begin
         @slice_max(b)
       end 
2×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0

julia> @chain df begin
         @slice_max(b, with_ties = false)
       end 
1×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0

julia> @chain df begin
         @slice_max(b, n = 3)
       end 
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
   
julia> @chain df begin
         @slice_max(b, prop = 0.5, missing_rm = true)
       end
3×3 DataFrame
 Row │ a         b         c        
     │ Float64?  Float64?  Float64? 
─────┼──────────────────────────────
   1 │      5.0       7.0       5.0
   2 │      6.0       7.0       6.0
   3 │      1.0       6.0       1.0
```

```
@slice_max(sql_query, column, n = 1)
```

指定された列の最大値を持つ行を選択します。これは常にタイを返します。

# 引数

  * `sql_query::SQLQuery`: 操作するSQLクエリ。
  * `column`: 最小値を特定するための列。
  * `n`: 各指定された列の最大値を持つ行の数。デフォルトは1で、最小値を持つ行を選択します。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());


julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @slice_max(value, n = 2)
         @arrange(groups)
         @collect
       end
4×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AJ      aa          5      1.0         1
   2 │ AD      aa          4      0.4         2
   3 │ AE      bb          5      0.5         1
   4 │ AI      bb          4      0.9         2

julia> @chain dt(db, df, "df_view") begin
         @slice_max(value)
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AE      bb          5      0.5         1
   2 │ AJ      aa          5      1.0         1

julia> @chain dt(db, df, "df_view") begin
        @filter(percent < .9)
        @slice_max(percent)
        @collect
       end
1×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AH      aa          3      0.8         1

julia>  @chain dt(db, df, "df_view") begin
         @group_by groups
         @slice_max(percent)
         @arrange groups
         @collect
       end
2×5 DataFrame
 Row │ id      groups  value  percent  rank_col 
     │ String  String  Int64  Float64  Int64    
─────┼──────────────────────────────────────────
   1 │ AJ      aa          5      1.0         1
   2 │ AI      bb          4      0.9         1

julia> @chain dt(db, df, "df_view") begin
         @summarize(percent_mean = mean(percent), _by = groups)
         @slice_max(percent_mean)
         @collect
       end
1×3 DataFrame
 Row │ groups  percent_mean  rank_col 
     │ String  Float64       Int64    
─────┼────────────────────────────────
   1 │ aa               0.6         1
```
