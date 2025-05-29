```
colmetadatakeys(df::AbstractDataFrame, [col::ColumnIndex])
colmetadatakeys(dfr::DataFrameRow, [col::ColumnIndex])
colmetadatakeys(dfc::DataFrameColumns, [col::ColumnIndex])
colmetadatakeys(dfr::DataFrameRows, [col::ColumnIndex])
```

`col` が渡された場合、列 `col` に設定されている列レベルのメタデータキーのイテレータを返します。`col` が渡されない場合、メタデータを持つすべての列に対して `col => colmetadatakeys(x, col)` ペアのイテレータを返します。ここで `col` は `Symbol` です。

値は [`colmetadata(df, col, key)`](@ref) を使用してアクセスできます。

`SubDataFrame` と `DataFrameRow` は親の `:note` スタイルのメタデータのみを公開します。

関連情報: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
