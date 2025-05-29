```
   @head(df, value)
```

データフレームの最初の n 行またはグループ化されたデータフレームの各グループの最初の n 行を表示します。

# 引数

  * `df`: データフレーム。
  * `value`: 返される行数。空白のままにするとデフォルトで 6 になります。

# 例

```
julia> df = DataFrame(a = vcat(repeat(["a"], inner = 4),
                                  repeat(["b"], inner = 4)),
                             b = 1:8)
8×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
   3 │ a           3
   4 │ a           4
   5 │ b           5
   6 │ b           6
   7 │ b           7
   8 │ b           8
   
julia> @head(df, 3)
3×2 DataFrame
 Row │ a        b     
     │ String?  Int64 
─────┼────────────────
   1 │ a            1
   2 │ a            2
   3 │ a            3

julia> @head(df)
6×2 DataFrame
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
   3 │ a           3
   4 │ a           4
   5 │ b           5
   6 │ b           6

julia> @chain df begin
         @group_by a
         @head 2
       end
GroupedDataFrame with 2 groups based on key: a
First Group (2 rows): a = "a"
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ a           1
   2 │ a           2
⋮
Last Group (2 rows): a = "b"
 Row │ a       b     
     │ String  Int64 
─────┼───────────────
   1 │ b           5
   2 │ b           6
```
