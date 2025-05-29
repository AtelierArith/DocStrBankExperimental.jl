```
@left_join(df1, df2, [by])
```

`df1`と`df2`の左結合をオプションの`by`を使って実行します。

# 引数

  * `df1`: DataFrame。
  * `df2`: DataFrame。
  * `by`: オプションの列または列のタプル。`by`は個々の列の補間をサポートします。`by`が指定されていない場合、`df1`と`df2`の間で共有される列名から推測されます。

# 例

```jldoctest
julia> df1 = DataFrame(a = ["a", "b"], b = 1:2);

julia> df2 = DataFrame(a = ["a", "c"], c = 3:4);
  
julia> @left_join(df1, df2)
2×3 DataFrame
 Row │ a       b      c       
     │ String  Int64  Int64?  
─────┼────────────────────────
   1 │ a           1        3
   2 │ b           2  missing 

julia> @left_join(df1, df2, a)
2×3 DataFrame
 Row │ a       b      c       
     │ String  Int64  Int64?  
─────┼────────────────────────
   1 │ a           1        3
   2 │ b           2  missing

julia> @left_join(df1, df2, a = a)
2×3 DataFrame
 Row │ a       b      c       
     │ String  Int64  Int64?  
─────┼────────────────────────
   1 │ a           1        3
   2 │ b           2  missing

julia> @left_join(df1, df2, "a")
2×3 DataFrame
 Row │ a       b      c       
     │ String  Int64  Int64?  
─────┼────────────────────────
   1 │ a           1        3
   2 │ b           2  missing

julia> @left_join(df1, df2, "a" = "a")
2×3 DataFrame
 Row │ a       b      c       
     │ String  Int64  Int64?  
─────┼────────────────────────
   1 │ a           1        3
   2 │ b           2  missing
```

```
@left_join(sql_query, join_table, orignal_table_col == new_table_col)
```

指定された条件に基づいて2つのSQLクエリの左結合を実行します。結合は等価結合または不等式結合が可能です。等価結合の場合、結合テーブルのキー列は削除されます。不等式結合は、`closest(key >= key2)`で不等式をラップすることによってAsOfまたはローリング結合にすることができます。不等式結合では、両方のテーブルからの列が保持されます。複数の結合基準を追加できますが、カンマで区切る必要があります。つまり、`closest(key >= key2), key3 == key3`

# 引数

  * `sql_query::SQLQuery`: 操作する主なSQLクエリ。
  * `join_table::{SQLQuery, String}`: 主なクエリテーブルと結合する二次SQLテーブル。データベースに既に存在するテーブルは、名前の文字列として記述する必要があります。
  * `orignal_table_col`: 結合に一致する元のテーブルの列。ベア列名または文字列として受け入れます。
  * `new_table_col`: 結合に一致する新しいテーブルの列。ベア列名または文字列として受け入れます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> df2 = DataFrame(id2 = ["AA", "AC", "AE", "AG", "AI", "AK", "AM"],
                category = ["X", "Y", "X", "Y", "X", "Y", "X"],
                score = [88, 92, 77, 83, 95, 68, 74]);

julia> db = connect(duckdb());

julia> dfm = dt(db, df, "df_mem"); dfj = dt(db, df2, "df_join");

julia> @chain dfm begin
         @left_join(t(dfj), id == id2 )
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  category  score   
     │ String  String  Int64  Float64  String?   Int64?  
─────┼───────────────────────────────────────────────────
   1 │ AA      bb          1      0.1  X              88
   2 │ AC      bb          3      0.3  Y              92
   3 │ AE      bb          5      0.5  X              77
   4 │ AG      bb          2      0.7  Y              83
   5 │ AI      bb          4      0.9  X              95
   6 │ AB      aa          2      0.2  missing   missing 
   7 │ AD      aa          4      0.4  missing   missing 
   8 │ AF      aa          1      0.6  missing   missing 
   9 │ AH      aa          3      0.8  missing   missing 
  10 │ AJ      aa          5      1.0  missing   missing 

julia> query = @chain dt(db, "df_join") begin
                  @filter(score > 85) # 結合テーブルで85を超えるスコアのみ表示
                end;

julia> @chain dfm begin
         @left_join(t(query), id == id2)
         @collect
       end
10×6 DataFrame
 Row │ id      groups  value  percent  category  score   
     │ String  String  Int64  Float64  String?   Int64?  
─────┼───────────────────────────────────────────────────
   1 │ AA      bb          1      0.1  X              88
   2 │ AC      bb          3      0.3  Y              92
   3 │ AI      bb          4      0.9  X              95
   4 │ AB      aa          2      0.2  missing   missing 
   5 │ AD      aa          4      0.4  missing   missing 
   6 │ AE      bb          5      0.5  missing   missing 
   7 │ AF      aa          1      0.6  missing   missing 
   8 │ AG      bb          2      0.7  missing   missing 
   9 │ AH      aa          3      0.8  missing   missing 
  10 │ AJ      aa          5      1.0  missing   missing 

julia>  @chain dfm begin
         @mutate(test = percent * 100)
         @left_join(t(dfj), test <= score, id = id2)
         @collect
       end;


julia>  @chain dfm begin
         @mutate(test = percent * 200)
         @left_join(t(dfj), closest(test >= score)) # asof join
         @collect
       end;
```
