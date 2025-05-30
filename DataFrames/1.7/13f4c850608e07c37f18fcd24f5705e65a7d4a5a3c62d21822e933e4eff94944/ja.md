```
metadata!(df::AbstractDataFrame, key::AbstractString, value; style::Symbol=:default)
metadata!(dfr::DataFrameRow, key::AbstractString, value; style::Symbol=:default)
metadata!(dfc::DataFrameColumns, key::AbstractString, value; style::Symbol=:default)
metadata!(dfr::DataFrameRows, key::AbstractString, value; style::Symbol=:default)
```

オブジェクト `df` のテーブルレベルのメタデータをキー `key` に対して値 `value` とスタイル `style`（デフォルトは `:default`）を持つように設定し、`df` を返します。

`SubDataFrame` と `DataFrameRow` では、`:note` スタイルのみが許可されています。異なるスタイルで親データフレームに既に存在するキー-バリューペアを設定しようとするとエラーが発生します。

参照: [`metadata`](@ref), [`metadatakeys`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

# 例

```jldoctest
julia> df = DataFrame(a=1, b=2);

julia> metadatakeys(df)
()

julia> metadata!(df, "name", "example", style=:note);

julia> metadatakeys(df)
KeySet for a Dict{String, Tuple{Any, Any}} with 1 entry. Keys:
  "name"

julia> metadata(df, "name")
"example"

julia> metadata(df, "name", style=true)
("example", :note)

julia> deletemetadata!(df, "name");

julia> metadatakeys(df)
()
```
