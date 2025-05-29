```
@anti_join(df1, df2, [by])
```

`df1`と`df2`の間でオプションの`by`を使用してアンチジョインを実行します。

# 引数

  * `df1`: DataFrame。
  * `df2`: DataFrame。
  * `by`: オプションの列または列のタプル。`by`は個々の列の補間をサポートします。`by`が指定されていない場合、`df1`と`df2`の間で共有される列名から推測されます。

# 例

```jldoctest
julia> df1 = DataFrame(a = ["a", "b"], b = 1:2);

julia> df2 = DataFrame(a = ["a", "c"], c = 3:4);
  
julia> @anti_join(df1, df2)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, a = a)
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2

julia> @anti_join(df1, df2, "a" = "a")
1×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           2
```

```
@anti_join(sql_query, join_table, orignal_table_col == new_table_col)
```

指定された条件に基づいて2つのSQLクエリの間でアンチジョインを実行します。ジョインは等価ジョインまたは不等号ジョインが可能です。等価ジョインの場合、結合テーブルのキー列は削除されます。不等号ジョインは、`closest(key >= key2)`で不等号をラップすることによってAsOfまたはローリングジョインにすることができます。不等号ジョインでは、両方のテーブルからの列が保持されます。複数の結合基準を追加できますが、カンマで区切る必要があります。つまり、`closest(key >= key2), key3 == key3`のようにします。

# 引数

  * `sql_query`: 操作する主なSQLクエリ。
  * `join_table::{SQLQuery, String}`: 主なクエリテーブルと結合する二次SQLテーブル。データベースに既に存在するテーブルは、名前の文字列として記述する必要があります。
  * `orignal_table_col`: 結合のために一致する元のテーブルの列。ベア列名または文字列として列を受け入れます。
  * `new_table_col`: 結合のために一致する新しいテーブルの列。ベア列名または文字列として列を受け入れます。

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


julia> dfj = dt(db, df2, "df_join");

julia> @chain dt(db, df, "df_view") begin
        @anti_join(t(dfj), id == id2)
        @collect
       end
5×4 DataFrame
 Row │ id      groups  value  percent 
     │ String  String  Int64  Float64 
─────┼────────────────────────────────
   1 │ AB      aa          2      0.2
   2 │ AD      aa          4      0.4
   3 │ AF      aa          1      0.6
   4 │ AH      aa          3      0.8
   5 │ AJ      aa          5      1.0
```
