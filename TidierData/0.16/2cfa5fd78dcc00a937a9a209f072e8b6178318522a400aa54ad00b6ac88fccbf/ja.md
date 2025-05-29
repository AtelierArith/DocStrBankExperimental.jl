```
@unnest_longer(df, columns, indices_include=false)
```

DataFrameの列にある配列をアンネストして、配列の各エントリに対して1行の長いDataFrameを作成します。

# 引数

  * `df`: DataFrame。
  * `columns`: アンネストする列。列のシンボルまたは値の数が一致する場合の列の範囲を指定できます。
  * `indices_include`: オプション。`true`に設定すると、各アンネストされた列のインデックス列が追加され、各配列エントリの位置が記録されます。
  * `keep_empty`: オプション。`true`に設定すると、空の配列を持つ行がスキップされずに保持され、欠損値としてアンネストされます。

# 例

```jldoctest
julia> df = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c      
     │ Int64  Array…  Array… 
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> @unnest_longer(df, 2)
4×3 DataFrame
 Row │ a      b      c      
     │ Int64  Int64  Array… 
─────┼──────────────────────
   1 │     1      1  [5, 6]
   2 │     1      2  [5, 6]
   3 │     2      3  [7, 8]
   4 │     2      4  [7, 8]

julia> @unnest_longer(df, b:c, indices_include = true)
4×5 DataFrame
 Row │ a      b      c      b_id   c_id  
     │ Int64  Int64  Int64  Int64  Int64 
─────┼───────────────────────────────────
   1 │     1      1      5      1      1
   2 │     1      2      6      2      2
   3 │     2      3      7      1      1
   4 │     2      4      8      2      2

julia> df2 = DataFrame(x = 1:4, y = [[], [1, 2, 3], [4, 5], Int[]])
4×2 DataFrame
 Row │ x      y            
     │ Int64  Array…       
─────┼─────────────────────
   1 │     1  Any[]
   2 │     2  Any[1, 2, 3]
   3 │     3  Any[4, 5]
   4 │     4  Any[]

julia> @unnest_longer(df2, y, keep_empty = true)
7×2 DataFrame
 Row │ x      y       
     │ Int64  Any     
─────┼────────────────
   1 │     1  missing 
   2 │     2  1
   3 │     2  2
   4 │     2  3
   5 │     3  4
   6 │     3  5
   7 │     4  missing 
```
