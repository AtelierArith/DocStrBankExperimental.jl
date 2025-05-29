```
n()
```

DataFrameの行数、またはGroupedDataFrameの文脈で使用される場合はグループ内の行数を返します。

# 引数

  * なし

# 例

```jldoctest
julia> df = DataFrame(a = repeat('a':'e', inner = 2), b = 1:10, c = 11:20);

julia> @chain df begin
         @summarize(n = n())
       end
1×1 DataFrame
 Row │ n     
     │ Int64 
─────┼───────
   1 │    10

julia> @chain df begin
         @group_by(a)
         @summarize(n = n())
       end
5×2 DataFrame
 Row │ a     n     
     │ Char  Int64 
─────┼─────────────
   1 │ a         2
   2 │ b         2
   3 │ c         2
   4 │ d         2
   5 │ e         2
```
