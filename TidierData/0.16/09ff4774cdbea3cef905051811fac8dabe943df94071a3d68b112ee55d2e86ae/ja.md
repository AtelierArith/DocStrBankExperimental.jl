```
@unnest_wider(df, columns, names_sep)
```

指定された配列または辞書の列を個別の列を持つ広い形式のデータフレームに展開します。

# 引数

  * `df`: データフレーム。
  * `columns`: 展開する列。これらの列は配列、辞書、データフレーム、またはタプルを含む必要があります。辞書の見出しは列名に変換されます。
  * `names_sep`: 新しい列名を作成するための区切り文字を指定するオプションの文字列。提供されない場合、デフォルトでは区切り文字はありません。

# 例

```jldoctest
julia> df = DataFrame(name = ["Zaki", "Farida"], attributes = [
               Dict("age" => 25, "city" => "New York"),
               Dict("age" => 30, "city" => "Los Angeles")]);

julia> @unnest_wider(df, attributes)
2×3 DataFrame
 Row │ name    city         age   
     │ String  String       Int64 
─────┼────────────────────────────
   1 │ Zaki    New York        25
   2 │ Farida  Los Angeles     30

julia> df2 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c      
     │ Int64  Array…  Array… 
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> @unnest_wider(df2, b:c, names_sep = "_")
2×5 DataFrame
 Row │ a      b_1    b_2    c_1    c_2   
     │ Int64  Int64  Int64  Int64  Int64 
─────┼───────────────────────────────────
   1 │     1      1      2      5      6
   2 │     2      3      4      7      8
```
