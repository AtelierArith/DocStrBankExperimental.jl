```
dropmissing!(df::AbstractDataFrame, cols=:; disallowmissing::Bool=true)
```

データフレーム `df` から欠損値を含む行を削除し、返します。

`cols` が指定されている場合、対応する列の欠損値のみが考慮されます。`cols` は任意の列セレクタ（`Symbol`、文字列または整数； `:`, `Cols`, `All`, `Between`, `Not`、正規表現、または `Symbol`、文字列または整数のベクター）を指定できます。

`disallowmissing` が `true`（デフォルト）である場合、`cols` 列は [`disallowmissing!`](@ref) を使用して変換されます。

メタデータ：この関数は、テーブルレベルおよび列レベルの `:note` スタイルのメタデータを保持します。

関連情報： [`dropmissing`](@ref) および [`completecases`](@ref)。

```jldoctest
julia> df = DataFrame(i=1:5,
                      x=[missing, 4, missing, 2, 1],
                      y=[missing, missing, "c", "d", "e"])
5×3 DataFrame
 Row │ i      x        y
     │ Int64  Int64?   String?
─────┼─────────────────────────
   1 │     1  missing  missing
   2 │     2        4  missing
   3 │     3  missing  c
   4 │     4        2  d
   5 │     5        1  e

julia> dropmissing!(copy(df))
2×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     4      2  d
   2 │     5      1  e

julia> dropmissing!(copy(df), disallowmissing=false)
2×3 DataFrame
 Row │ i      x       y
     │ Int64  Int64?  String?
─────┼────────────────────────
   1 │     4       2  d
   2 │     5       1  e

julia> dropmissing!(copy(df), :x)
3×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String?
─────┼───────────────────────
   1 │     2      4  missing
   2 │     4      2  d
   3 │     5      1  e

julia> dropmissing!(df, [:x, :y])
2×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     4      2  d
   2 │     5      1  e
```
