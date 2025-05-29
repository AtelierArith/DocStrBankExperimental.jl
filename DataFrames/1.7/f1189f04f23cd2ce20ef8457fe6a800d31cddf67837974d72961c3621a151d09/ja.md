```
emptymetadata!(df::AbstractDataFrame)
emptymetadata!(dfr::DataFrameRow)
emptymetadata!(dfc::DataFrameColumns)
emptymetadata!(dfr::DataFrameRows)
```

オブジェクト `df` からすべてのテーブルレベルのメタデータを削除します。

`SubDataFrame` と `DataFrameRow` については、親からの `:note` スタイルのメタデータのみ削除できます（他のスタイルはビューに伝播しないため）。

参照: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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

julia> emptymetadata!(df);

julia> metadatakeys(df)
()
```
