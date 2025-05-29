```
dropmissing(df::AbstractDataFrame, cols=:; view::Bool=false, disallowmissing::Bool=!view)
```

`df`の欠損値を含む行を除外したデータフレームを返します。

`cols`が指定されている場合、対応する列の欠損値のみが考慮されます。`cols`は任意の列セレクタ（`Symbol`、文字列または整数；`:`, `Cols`, `All`, `Between`, `Not`、正規表現、または`Symbol`、文字列または整数のベクター）を指定できます。

`view=false`の場合、新しく割り当てられた`DataFrame`が返されます。`view=true`の場合、`df`への`SubDataFrame`ビューが返されます。この場合、`disallowmissing`は`false`でなければなりません。

`disallowmissing`が`true`の場合（`view`が`false`のときのデフォルト）、`cols`で指定された列は欠損値を許可しないように変換されます [`disallowmissing!`](@ref) を使用します。

関連情報: [`completecases`](@ref) と [`dropmissing!`](@ref) を参照してください。

メタデータ: この関数はテーブルレベルおよび列レベルの`:note`スタイルのメタデータを保持します。

# 例

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

julia> dropmissing(df)
2×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     4      2  d
   2 │     5      1  e

julia> dropmissing(df, disallowmissing=false)
2×3 DataFrame
 Row │ i      x       y
     │ Int64  Int64?  String?
─────┼────────────────────────
   1 │     4       2  d
   2 │     5       1  e

julia> dropmissing(df, :x)
3×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String?
─────┼───────────────────────
   1 │     2      4  missing
   2 │     4      2  d
   3 │     5      1  e

julia> dropmissing(df, [:x, :y])
2×3 DataFrame
 Row │ i      x      y
     │ Int64  Int64  String
─────┼──────────────────────
   1 │     4      2  d
   2 │     5      1  e
```
