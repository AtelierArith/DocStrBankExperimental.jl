```
@group_by(df, exprs...)
```

ユニークな `cols` のセットによって指定されたグループで操作が行われる `GroupedDataFrame` を返します。

# 引数

  * `df`: DataFrame。
  * `exprs...`: グループ化するためのDataFrameの列または整然とした式。単一の整然とした式またはカンマで区切られた複数の式であることができます。

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
