```
@group_by(sql_query, columns...)
```

指定された列でSQLテーブルの行をグループ化します。グループ化が端末操作として行われ、その後の変異や要約が行われない場合（以下の例のように）、結果のデータフレームにはそのグループのみが含まれます。グループ化の後に収集を行うと、TidierDataのようにグループ化されたデータフレームは返されません。

# 引数

  * `sql_query`: 操作するSQLクエリ。
  * `exprs`: グループ化する列を指定する式。列は名前で指定できます。

# 例

```jldoctest
julia> df = DataFrame(id = [string('A' + i ÷ 26, 'A' + i % 26) for i in 0:9], 
                        groups = [i % 2 == 0 ? "aa" : "bb" for i in 1:10], 
                        value = repeat(1:5, 2), 
                        percent = 0.1:0.1:1.0);

julia> db = connect(duckdb());

julia> @chain dt(db, df, "df_view") begin
         @group_by(groups)
         @arrange(groups)
         @collect
       end
2×1 DataFrame
 Row │ groups 
     │ String 
─────┼────────
   1 │ aa
   2 │ bb

julia> @chain dt(db, df, "df_view") begin
         @group_by(big_val = if_else(value > 3, "big", "small"))
         @summarise(n=n())
         @arrange(big_val)
         @collect
       end
2×2 DataFrame
 Row │ big_val  n     
     │ String   Int64 
─────┼────────────────
   1 │ big          4
   2 │ small        6
```
