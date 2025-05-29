```
separate_rows(df, columns..., sep)
```

指定された列の内容を、与えられた区切り文字に基づいて複数の行に分割します。

# 引数

  * `df`: DataFrame
  * `columns`: 分割する列または複数の列。整数と列名の混合が可能です。
  * `sep`: 列の値を分割するために使用される文字列、文字、または正規表現。

# 例

```jldoctest
julia> df = DataFrame(a = 1:3,
                      b = ["a", "aa;bb;cc", "dd;ee"],
                      c = ["1", "2;3;4", "5;6"],
                      d = ["7", "8;9;10", "11;12"])
3×4 DataFrame
 Row │ a      b         c       d      
     │ Int64  String    String  String 
─────┼─────────────────────────────────
   1 │     1  a         1       7
   2 │     2  aa;bb;cc  2;3;4   8;9;10
   3 │     3  dd;ee     5;6     11;12

julia> @separate_rows(df, 2, 4, ";")
6×4 DataFrame
 Row │ a      b          c       d         
     │ Int64  SubStrin…  String  SubStrin… 
─────┼─────────────────────────────────────
   1 │     1  a          1       7
   2 │     2  aa         2;3;4   8
   3 │     2  bb         2;3;4   9
   4 │     2  cc         2;3;4   10
   5 │     3  dd         5;6     11
   6 │     3  ee         5;6     12

julia> @separate_rows(df, b:d, ";")
6×4 DataFrame
 Row │ a      b          c          d         
     │ Int64  SubStrin…  SubStrin…  SubStrin… 
─────┼────────────────────────────────────────
   1 │     1  a          1          7
   2 │     2  aa         2          8
   3 │     2  bb         3          9
   4 │     2  cc         4          10
   5 │     3  dd         5          11
   6 │     3  ee         6          12
```
