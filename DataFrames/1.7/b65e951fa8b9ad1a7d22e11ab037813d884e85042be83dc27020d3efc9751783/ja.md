```
vcat(dfs::AbstractDataFrame...;
     cols::Union{Symbol, AbstractVector{Symbol},
                 AbstractVector{<:AbstractString}}=:setequal,
     source::Union{Nothing, Symbol, AbstractString,
                   Pair{<:Union{Symbol, AbstractString}, <:AbstractVector}}=nothing)
```

`AbstractDataFrame`を縦に連結します。

`cols`キーワード引数は、返されるデータフレームの列を決定します：

  * `:setequal`: すべてのデータフレームが順序を無視して同じ列名を持つことを要求します。異なる順序で現れる場合、最初に提供されたデータフレームの順序が使用されます。
  * `:orderequal`: すべてのデータフレームが同じ列名を持ち、同じ順序であることを要求します。
  * `:intersect`: 提供されたすべてのデータフレームに存在する列のみが保持されます。交差が空の場合、空のデータフレームが返されます。
  * `:union`: 提供されたデータフレームのうち*少なくとも1つ*に存在する列が保持されます。いくつかのデータフレームに存在しない列は、必要に応じて`missing`で埋められます。
  * `Symbol`または文字列のベクター: リストされた列のみが保持されます。いくつかのデータフレームに存在しない列は、必要に応じて`missing`で埋められます。

`source`キーワード引数は、`nothing`（デフォルト）でない場合、結果のデータフレームの最後の位置に追加される列を指定し、ソースデータフレームを識別します。これは`Symbol`または`AbstractString`であり、その場合、識別子は渡されたソースデータフレームの番号になります。または、`Symbol`または`AbstractString`とデータフレーム識別子を指定するベクターからなる`Pair`であることもできます（これらは一意である必要はありません）。ソース列の名前は、いかなるソースデータフレームにも存在してはなりません。

列の順序は、含まれるデータフレームに現れる順序によって決定され、最初のデータフレームのヘッダーを検索し、次に2番目、などとなります。

列の要素型は、`vcat`が`AbstractVector`に対して行うように`promote_type`を使用して決定されます。

`vcat`は、結果を構成する際に空のデータフレームを無視します（メタデータを除く）ので、ループの最初に空のデータフレームを初期化し、それに`vcat`することが可能です。

メタデータ: `vcat`は、すべての渡されたデータフレームに存在し、同じ値を持つキーに対してテーブルレベルの`:note`スタイルのメタデータを伝播します。`vcat`は、この列を含むすべての渡されたデータフレームに存在し、同じ値を持つキーに対して列レベルの`:note`スタイルのメタデータを伝播します。

# 例

```jldoctest
julia> df1 = DataFrame(A=1:3, B=1:3)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> df2 = DataFrame(A=4:6, B=4:6)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     4      4
   2 │     5      5
   3 │     6      6

julia> df3 = DataFrame(A=7:9, C=7:9)
3×2 DataFrame
 Row │ A      C
     │ Int64  Int64
─────┼──────────────
   1 │     7      7
   2 │     8      8
   3 │     9      9

julia> df4 = DataFrame()
0×0 DataFrame

julia> vcat(df1, df2)
6×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3
   4 │     4      4
   5 │     5      5
   6 │     6      6

julia> vcat(df1, df3, cols=:union)
6×3 DataFrame
 Row │ A      B        C
     │ Int64  Int64?   Int64?
─────┼─────────────────────────
   1 │     1        1  missing
   2 │     2        2  missing
   3 │     3        3  missing
   4 │     7  missing        7
   5 │     8  missing        8
   6 │     9  missing        9

julia> vcat(df1, df3, cols=:intersect)
6×1 DataFrame
 Row │ A
     │ Int64
─────┼───────
   1 │     1
   2 │     2
   3 │     3
   4 │     7
   5 │     8
   6 │     9

julia> vcat(df4, df1)
3×2 DataFrame
 Row │ A      B
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      2
   3 │     3      3

julia> vcat(df1, df2, df3, df4, cols=:union, source="source")
9×4 DataFrame
 Row │ A      B        C        source
     │ Int64  Int64?   Int64?   Int64
─────┼─────────────────────────────────
   1 │     1        1  missing       1
   2 │     2        2  missing       1
   3 │     3        3  missing       1
   4 │     4        4  missing       2
   5 │     5        5  missing       2
   6 │     6        6  missing       2
   7 │     7  missing        7       3
   8 │     8  missing        8       3
   9 │     9  missing        9       3

julia> vcat(df1, df2, df4, df3, cols=:union, source=:source => 'a':'d')
9×4 DataFrame
 Row │ A      B        C        source
     │ Int64  Int64?   Int64?   Char
─────┼─────────────────────────────────
   1 │     1        1  missing  a
   2 │     2        2  missing  a
   3 │     3        3  missing  a
   4 │     4        4  missing  b
   5 │     5        5  missing  b
   6 │     6        6  missing  b
   7 │     7  missing        7  d
   8 │     8  missing        8  d
   9 │     9  missing        9  d
```
