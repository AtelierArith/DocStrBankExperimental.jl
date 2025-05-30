```
flatten(df::AbstractDataFrame, cols; scalar::Type=Union{})
```

データフレーム `df` の列 `cols` に iterable 要素があり、それが `length` を定義している場合（例えば、`Vector` の `Vector`）、各 `col` の各要素がフラット化された `DataFrame` を返します。つまり、`col` に対応する列は、元のエントリが連結された長いベクターになります。`df` の行 `i` の `cols` 以外の列の要素は、`df[i, col]` の長さに応じて繰り返されます。したがって、これらの長さは `cols` の各 `col` に対して同じでなければならず、そうでない場合はエラーが発生します。これらの要素はコピーされず、したがって、変更可能な場合、返された `DataFrame` で変更すると `df` に影響を与えます。

`cols` は任意の列セレクタ（`Symbol`、文字列または整数；`:`, `Cols`, `All`, `Between`, `Not`、正規表現、または `Symbol`、文字列または整数のベクター）で指定できます。

`scalar` が渡されると、フラット化された列にこの型の値がある場合、それはスカラーとして扱われ、他の列に格納されている値の長さに合わせて必要な回数だけブロードキャストされます。行内のすべての値がスカラーである場合、1つの行が生成されます。

メタデータ：この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

# 例

```jldoctest
julia> df1 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7, 8]])
2×3 DataFrame
 Row │ a      b       c
     │ Int64  Array…  Array…
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7, 8]

julia> flatten(df1, :b)
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Array…
─────┼──────────────────────
   1 │     1      1  [5, 6]
   2 │     1      2  [5, 6]
   3 │     2      3  [7, 8]
   4 │     2      4  [7, 8]

julia> flatten(df1, [:b, :c])
4×3 DataFrame
 Row │ a      b      c
     │ Int64  Int64  Int64
─────┼─────────────────────
   1 │     1      1      5
   2 │     1      2      6
   3 │     2      3      7
   4 │     2      4      8

julia> df2 = DataFrame(a=[1, 2], b=[("p", "q"), ("r", "s")])
2×2 DataFrame
 Row │ a      b
     │ Int64  Tuple…
─────┼───────────────────
   1 │     1  ("p", "q")
   2 │     2  ("r", "s")

julia> flatten(df2, :b)
4×2 DataFrame
 Row │ a      b
     │ Int64  String
─────┼───────────────
   1 │     1  p
   2 │     1  q
   3 │     2  r
   4 │     2  s

julia> df3 = DataFrame(a=[1, 2], b=[[1, 2], [3, 4]], c=[[5, 6], [7]])
2×3 DataFrame
 Row │ a      b       c
     │ Int64  Array…  Array…
─────┼───────────────────────
   1 │     1  [1, 2]  [5, 6]
   2 │     2  [3, 4]  [7]

julia> flatten(df3, [:b, :c])
ERROR: ArgumentError: Lengths of iterables stored in columns :b and :c are not the same in row 2

julia> df4 = DataFrame(a=[1, 2, 3],
                       b=[[1, 2], missing, missing],
                       c=[[5, 6], missing, [7, 8]])
3×3 DataFrame
 Row │ a      b        c
     │ Int64  Array…?  Array…?
─────┼─────────────────────────
   1 │     1  [1, 2]   [5, 6]
   2 │     2  missing  missing
   3 │     3  missing  [7, 8]

julia> flatten(df4, [:b, :c], scalar=Missing)
5×3 DataFrame
 Row │ a      b        c
     │ Int64  Int64?   Int64?
─────┼─────────────────────────
   1 │     1        1        5
   2 │     1        2        6
   3 │     2  missing  missing
   4 │     3  missing        7
   5 │     3  missing        8
```
