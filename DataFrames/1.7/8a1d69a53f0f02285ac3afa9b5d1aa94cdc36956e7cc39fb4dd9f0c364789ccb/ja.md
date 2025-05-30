```
emptycolmetadata!(df::AbstractDataFrame, [col::ColumnIndex])
emptycolmetadata!(dfr::DataFrameRow, [col::ColumnIndex])
emptycolmetadata!(dfc::DataFrameColumns, [col::ColumnIndex])
emptycolmetadata!(dfr::DataFrameRows, [col::ColumnIndex])
```

`df`の列`col`とキー`key`に設定された列レベルのメタデータを削除し、`df`を返します。

`SubDataFrame`および`DataFrameRow`については、親からの`:note`スタイルのメタデータのみが削除できます（他のスタイルはビューに伝播しないため）。

関連情報: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref).

# 例

```jldoctest
julia> df = DataFrame(a=1, b=2);

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

julia> emptycolmetadata!(df, :a);

julia> colmetadatakeys(df)
()
```
