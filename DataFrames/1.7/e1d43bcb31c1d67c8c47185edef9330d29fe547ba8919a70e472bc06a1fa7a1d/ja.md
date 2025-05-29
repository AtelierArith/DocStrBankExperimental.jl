```
names(df::AbstractDataFrame, cols=:)
names(df::DataFrameRow, cols=:)
names(df::GroupedDataFrame, cols=:)
names(df::DataFrameRows, cols=:)
names(df::DataFrameColumns, cols=:)
names(df::GroupKey)
```

`df`に含まれる列の名前の新しく割り当てられた`Vector{String}`を返します。

`cols`が渡された場合、返される列名はセレクタに一致するものに制限されます（これは特に正規表現、`Cols`、`Not`、および`Between`で便利です）。`cols`は次のように指定できます：

  * 任意の列セレクタ（`Symbol`、文字列、または整数；`:`, `Cols`, `All`, `Between`, `Not`、正規表現、または`Symbol`、文字列、または整数のベクター）；これらの列セレクタは[一般的なルール](@ref)セクションの[インデクシング](@ref)部分のDataFrames.jlマニュアルに文書化されています
  * `Type`の場合、その`eltype`が`T`のサブタイプである列の名前が返されます
  * 列名を文字列として受け取り、保持すべき列に対して`true`を返す`Function`述語

また、`GroupedDataFrame`の場合は`Symbol.(names(df))`を使用する必要があることを除いて、`Vector{Symbol}`を返す[`propertynames`](@ref)も参照してください。

# 例

```jldoctest
julia> df = DataFrame(x1=[1, missing, missing], x2=[3, 2, 4], x3=[3, missing, 2], x4=Union{Int, Missing}[2, 4, 4])
3×4 DataFrame
 Row │ x1       x2     x3       x4
     │ Int64?   Int64  Int64?   Int64?
─────┼─────────────────────────────────
   1 │       1      3        3       2
   2 │ missing      2  missing       4
   3 │ missing      4        2       4

julia> names(df)
4-element Vector{String}:
 "x1"
 "x2"
 "x3"
 "x4"

julia> names(df, Int) # 要素の型がIntである列を選択
1-element Vector{String}:
 "x2"

julia> names(df, x -> x[end] == '2') # 名前の最後の文字が'2'である列を選択
1-element Vector{String}:
 "x2"

julia> fun(col) = sum(skipmissing(col)) >= 10
fun (generic function with 1 method)

julia> names(df, fun.(eachcol(df))) # 要素の合計が少なくとも10である列を選択
1-element Vector{String}:
 "x4"

julia> names(df, eltype.(eachcol(df)) .>: Missing) # 欠損値を許可する列を選択
3-element Vector{String}:
 "x1"
 "x3"
 "x4"

julia> names(df, any.(ismissing, eachcol(df))) # 欠損値を含む列を選択
2-element Vector{String}:
 "x1"
 "x3"
```
