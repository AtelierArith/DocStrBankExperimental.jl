```
@anti_join(sql_query, join_table, orignal_table_col == new_table_col)
```

指定された条件に基づいて2つのSQLクエリの間でアンチジョインを実行します。ジョインは等価ジョインまたは不等号ジョインが可能です。等価ジョインの場合、結合テーブルのキー列は削除されます。不等号ジョインは、`closest(key >= key2)`で不等号をラップすることによって、AsOfまたはローリングジョインに変えることができます。不等号ジョインでは、両方のテーブルからの列が保持されます。複数の結合基準を追加することができますが、カンマで区切る必要があります。つまり、`closest(key >= key2), key3 == key3`のようにします。

# 引数

  * `sql_query`: 操作する主なSQLクエリ。
  * `join_table::{SQLQuery, String}`: 主なクエリテーブルと結合する二次SQLテーブル。データベースに既に存在するテーブルは、名前の文字列として記述する必要があります。
  * `orignal_table_col`: 結合に一致する元のテーブルの列。コラムはベアコラム名または文字列として受け入れられます。
  * `new_table_col`: 結合に一致する新しいテーブルの列。コラムはベアコラム名または文字列として受け入れられます。

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
