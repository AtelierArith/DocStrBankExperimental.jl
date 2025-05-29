```
  @unite(df, new_cols, from_cols, sep, remove = true)
```

特定の区切り文字を使用して複数の列を1つの新しい列に分割します

# 引数

  * `df`: DataFrame
  * `new_col`: 組み合わせを受け取る新しい列
  * `from_cols`: 組み合わせる列名、[]または()をサポート
  * `sep`: 新しい列の値を区切る文字列または文字
  * `remove`: デフォルトは`true`、データフレームから入力列を削除します

# 例

```jldoctest
julia> df = DataFrame( b = ["1", "2", "3"], c = ["1", "2", "3"], d = [missing, missing, "3"]);

julia> @unite(df, new_col, (b, c, d), "-")
3×1 DataFrame
 Row │ new_col 
     │ String  
─────┼─────────
   1 │ 1-1
   2 │ 2-2
   3 │ 3-3-3
   
julia> @unite(df, new_col, (b, c, d), "-", remove = false)
3×4 DataFrame
 Row │ b       c       d        new_col 
     │ String  String  String?  String  
─────┼──────────────────────────────────
   1 │ 1       1       missing  1-1
   2 │ 2       2       missing  2-2
   3 │ 3       3       3        3-3-3
```
