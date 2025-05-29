```
eachcol(df::AbstractDataFrame)
```

`AbstractDataFrame`の列を列ごとに反復処理できるベクトルのような`DataFrameColumns`オブジェクトを返します。

整数、`Symbol`、または文字列を使用して`DataFrameColumns`オブジェクトにインデックスを付けると、対応する列が返されます（コピーなし）。複数の列セレクタを使用して`DataFrameColumns`オブジェクトにインデックスを付けると、選択された列のみを含む新しい親を持つ部分的な`DataFrameColumns`オブジェクトが返されます（コピーなし）。

`DataFrameColumns`はほとんどの`AbstractVector` APIをサポートしています。主な違いは、読み取り専用であり、`keys`関数が`Symbol`のベクトルを返すこと（通常のベクトルの場合は整数ではない）です。

特に、`findnext`、`findprev`、`findfirst`、`findlast`、および`findall`関数がサポートされており、`findnext`および`findprev`関数では整数、文字列、または`Symbol`を参照インデックスとして渡すことが許可されています。

# 例

```jldoctest
julia> df = DataFrame(x=1:4, y=11:14)
4×2 DataFrame
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> eachcol(df)
4×2 DataFrameColumns
 Row │ x      y
     │ Int64  Int64
─────┼──────────────
   1 │     1     11
   2 │     2     12
   3 │     3     13
   4 │     4     14

julia> collect(eachcol(df))
2-element Vector{AbstractVector}:
 [1, 2, 3, 4]
 [11, 12, 13, 14]

julia> map(eachcol(df)) do col
           maximum(col) - minimum(col)
       end
2-element Vector{Int64}:
 3
 3

julia> sum.(eachcol(df))
2-element Vector{Int64}:
 10
 50
```
