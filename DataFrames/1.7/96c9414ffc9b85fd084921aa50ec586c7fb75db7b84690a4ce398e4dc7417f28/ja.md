```
colmetadata!(df::AbstractDataFrame, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfr::DataFrameRow, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfc::DataFrameColumns, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfr::DataFrameRows, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
```

`df`の列`col`に対して、キー`key`の列レベルメタデータを値`value`およびスタイル`style`（デフォルトは`:default`）に設定し、`df`を返します。

`SubDataFrame`および`DataFrameRow`の場合、`:note`スタイルのみが許可されています。異なるスタイルで親データフレームに既に存在するキー-バリューペアを設定しようとするとエラーが発生します。

参照: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

# 例

```jldoctest
julia> df = DataFrame(a=1, b=2);

julia> colmetadatakeys(df)
()

julia> colmetadata!(df, :a, "name", "example", style=:note);

julia> collect(colmetadatakeys(df))
1-element Vector{Pair{Symbol, Base.KeySet{String, Dict{String, Tuple{Any, Any}}}}}:
 :a => ["name"]

julia> colmetadatakeys(df, :a)
KeySet for a Dict{String, Tuple{Any, Any}} with 1 entry. Keys:
  "name"

julia> colmetadata(df, :a, "name")
"example"

julia> colmetadata(df, :a, "name", style=true)
("example", :note)

julia> deletecolmetadata!(df, :a, "name");

julia> colmetadatakeys(df)
()
```
