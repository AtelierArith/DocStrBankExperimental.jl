```
@group_by(df, exprs...)
```

ユニークな `cols` のセットによって指定されたグループで操作が行われる `GroupedDataFrame` を返します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: グループ化するためのDataFrameの列または整然とした式。単一の整然とした式またはカンマで区切られた複数の式を指定できます。

# 例

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);

julia> @chain df begin
         @group_by(a)
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0  

julia> @chain df begin
         @group_by(d = uppercase(a))
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ d     b       
     │ Char  Float64 
─────┼───────────────
   1 │ A         1.0
   2 │ B         2.0
   3 │ C         3.0
   4 │ D         4.0
   5 │ E         5.0

julia> @chain df begin
         @group_by(-(b, c)) # same as `a`
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0

julia> @chain df begin
         @group_by(!(b, c)) # same as `a`
         @summarize(b = mean(b))
       end
5×2 DataFrame
 Row │ a     b       
     │ Char  Float64 
─────┼───────────────
   1 │ a         1.0
   2 │ b         2.0
   3 │ c         3.0
   4 │ d         4.0
   5 │ e         5.0
```

```
@group_by(sql_query, columns...)
```

指定された列によってSQLテーブルの行をグループ化します。グループ化が端末操作として行われ、その後の変異または要約が行われない場合（以下の例のように）、結果のデータフレームにはそのグループのみが含まれます。グループ化の後に収集を行うと、TidierDataのようにグループ化されたデータフレームは返されません。

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
