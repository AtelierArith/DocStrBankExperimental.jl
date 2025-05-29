@fill_missing(df, [columns...], direction)

DataFrame `df` の欠損値を指定された方法で埋めます。

# 引数

  * `df`: 欠損値を埋めたい DataFrame または GroupedDataFrame。
  * `columns`: (オプション) 欠損値を埋める必要がある列をカンマで区切って指定します。指定しない場合、操作はすべての列に適用されます。
  * `direction`: 欠損値を埋めるために使用する方法を含む文字列。オプションには、「down」（最後の観測値を前方に持ち越す）または「up」（次の観測値を後方に持ち越す）が含まれます。

# 例

```jldoctest
julia> df = DataFrame(
          dt1 = [missing, 0.2, missing, missing, 1, missing, 5, 6],
          dt2 = [0.3, 2, missing, 3, missing, 5, 6,missing],
          dt3 = [missing, 0.2, missing, missing, 1, missing, 5, 6],
          dt4 = [0.3, missing, missing, 3, missing, 5, 6, missing],
          dt5 = ['a', 'b', 'a', 'b', 'a', 'a', 'a', 'b']);

julia> @fill_missing(df, dt2, dt4, "down")
8×5 DataFrame
 Row │ dt1        dt2       dt3        dt4       dt5  
     │ Float64?   Float64?  Float64?   Float64?  Char 
─────┼────────────────────────────────────────────────
   1 │ missing         0.3  missing         0.3  a
   2 │       0.2       2.0        0.2       0.3  b
   3 │ missing         2.0  missing         0.3  a
   4 │ missing         3.0  missing         3.0  b
   5 │       1.0       3.0        1.0       3.0  a
   6 │ missing         5.0  missing         5.0  a
   7 │       5.0       6.0        5.0       6.0  a
   8 │       6.0       6.0        6.0       6.0  b

julia> @chain df begin
         @fill_missing("up")
       end
8×5 DataFrame
 Row │ dt1       dt2        dt3       dt4        dt5  
     │ Float64?  Float64?   Float64?  Float64?   Char 
─────┼────────────────────────────────────────────────
   1 │      0.2        0.3       0.2        0.3  a
   2 │      0.2        2.0       0.2        3.0  b
   3 │      1.0        3.0       1.0        3.0  a
   4 │      1.0        3.0       1.0        3.0  b
   5 │      1.0        5.0       1.0        5.0  a
   6 │      5.0        5.0       5.0        5.0  a
   7 │      5.0        6.0       5.0        6.0  a
   8 │      6.0  missing         6.0  missing    b 

julia> @chain df begin
         @group_by(dt5)
         @fill_missing(dt1, "up")
       end
GroupedDataFrame with 2 groups based on key: dt5
First Group (5 rows): dt5 = 'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)
 Row │ dt1       dt2        dt3        dt4        dt5  
     │ Float64?  Float64?   Float64?   Float64?   Char 
─────┼─────────────────────────────────────────────────
   1 │      1.0        0.3  missing          0.3  a
   2 │      1.0  missing    missing    missing    a
   3 │      1.0  missing          1.0  missing    a
   4 │      5.0        5.0  missing          5.0  a
   5 │      5.0        6.0        5.0        6.0  a
⋮
Last Group (3 rows): dt5 = 'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)
 Row │ dt1       dt2        dt3        dt4        dt5  
     │ Float64?  Float64?   Float64?   Float64?   Char 
─────┼─────────────────────────────────────────────────
   1 │      0.2        2.0        0.2  missing    b
   2 │      6.0        3.0  missing          3.0  b
   3 │      6.0  missing          6.0  missing    b
```
