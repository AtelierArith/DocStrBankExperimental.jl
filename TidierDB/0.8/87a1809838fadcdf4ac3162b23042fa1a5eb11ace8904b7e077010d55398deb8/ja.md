```
@inner_join(sql_query, join_table, orignal_table_col == new_table_col)
```

指定された条件に基づいて2つのSQLクエリの間で内部結合を実行します。結合は等価結合または不等式結合が可能です。等価結合の場合、結合テーブルのキー列は削除されます。不等式結合は、最も近いキーを使用してAsOfまたはローリング結合にすることができます。 不等式結合では、両方のテーブルからの列が保持されます。複数の結合基準を追加できますが、カンマで区切る必要があります。つまり、`closest(key >= key2), key3 == key3`

# 引数

  * `sql_query`: 操作する主なSQLクエリ。
  * `join_table::{SQLQuery, String}`: 主なクエリテーブルと結合する二次SQLテーブル。データベースに既に存在するテーブルは、名前の文字列として記述する必要があります。
  * `orignal_table_col`: 結合に一致する元のテーブルの列。ベア列名または文字列として列を受け入れます。
  * `new_table_col`: 結合に一致する新しいテーブルの列。ベア列名または文字列として列を受け入れます。

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
         @inner_join(t(dfj), id == id2)
         @collect
       end
5×6 DataFrame
 Row │ id      groups  value  percent  category  score 
     │ String  String  Int64  Float64  String    Int64 
─────┼─────────────────────────────────────────────────
   1 │ AA      bb          1      0.1  X            88
   2 │ AC      bb          3      0.3  Y            92
   3 │ AE      bb          5      0.5  X            77
   4 │ AG      bb          2      0.7  Y            83
   5 │ AI      bb          4      0.9  X            95
```
