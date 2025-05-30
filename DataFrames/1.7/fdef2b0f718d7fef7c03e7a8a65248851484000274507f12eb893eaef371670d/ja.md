```
deletemetadata!(df::AbstractDataFrame, key::AbstractString)
deletemetadata!(dfr::DataFrameRow, key::AbstractString)
deletemetadata!(dfc::DataFrameColumns, key::AbstractString)
deletemetadata!(dfr::DataFrameRows, key::AbstractString)
```

オブジェクト `df` からキー `key` のテーブルレベルのメタデータを削除し、`df` を返します。キーが存在しない場合は、変更せずに `df` を返します。

`SubDataFrame` と `DataFrameRow` については、親からの `:note` スタイルのメタデータのみが削除できます（他のスタイルはビューに伝播しないため）。

参照: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
