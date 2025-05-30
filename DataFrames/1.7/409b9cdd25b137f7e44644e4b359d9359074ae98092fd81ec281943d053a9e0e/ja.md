```
completecases(df::AbstractDataFrame, cols=:)
```

データフレーム `df` において、欠損値のない行（完全なケース）を示す `true` エントリを持つブールベクターを返します。

`cols` が指定されている場合、対応する列の欠損値のみが考慮されます。`cols` は、`df` に少なくとも1つの列がある場合に少なくとも1つの列を返す任意の列セレクタ（`Symbol`、文字列または整数； `:`、`Cols`、`All`、`Between`、`Not`、正規表現、または `Symbol`、文字列または整数のベクター）を指定できます。

関連情報: [`dropmissing`](@ref) および [`dropmissing!`](@ref)。行のインデックスを取得するには `findall(completecases(df))` を使用します。

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

julia> completecases(df)
5-element BitVector:
 0
 0
 0
 1
 1

julia> completecases(df, :x)
5-element BitVector:
 0
 1
 0
 1
 1

julia> completecases(df, [:x, :y])
5-element BitVector:
 0
 0
 0
 1
 1
```
