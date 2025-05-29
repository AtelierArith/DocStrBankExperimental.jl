```
@bind_rows(dfs..., id)
```

複数のDataFrameを行で結合します。

提供されたDataFrameのいずれかに存在する列は保持されます。いくつかのDataFrameに存在しない列は、必要に応じて欠損値で埋められます。

# 引数

  * `dfs...`: 結合するDataFrame。
  * `id`: 文字列のDataFrame識別子。idが指定されると、各行を元のDataFrameにリンクするための数値識別子の新しい列が作成されます。

# 例

```jldoctest bind_rows
julia> df1 = DataFrame(a=1:3, b=1:3);

julia> df2 = DataFrame(a=4:6, b=4:6);

julia> df3 = DataFrame(a=7:9, c=7:9);

julia> @chain df1 begin
         @bind_rows(df2)
       end
6×2 DataFrame
 Row │ a      b     
     │ Int64  Int64 
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      5
   6 │     6      6
```

列がいくつかのDataFrameに存在しない場合、それらは欠損値で埋められます。

```jldoctest bind_rows
julia> @chain df1 begin
         @bind_rows(df2, df3)
       end
9×3 DataFrame
 Row │ a      b        c       
     │ Int64  Int64?   Int64?  
─────┼─────────────────────────
   1 │     1        1  missing 
   2 │     2        2  missing 
   3 │     3        3  missing 
   4 │     4        4  missing 
   5 │     5        5  missing 
   6 │     6        6  missing 
   7 │     7  missing        7
   8 │     8  missing        8
   9 │     9  missing        9

julia> @chain df1 begin
         @bind_rows(df2, df3, id = "id")
       end
9×4 DataFrame
 Row │ a      b        c        id    
     │ Int64  Int64?   Int64?   Int64 
─────┼────────────────────────────────
   1 │     1        1  missing      1
   2 │     2        2  missing      1
   3 │     3        3  missing      1
   4 │     4        4  missing      2
   5 │     5        5  missing      2
   6 │     6        6  missing      2
   7 │     7  missing        7      3
   8 │     8  missing        8      3
   9 │     9  missing        9      3
```
