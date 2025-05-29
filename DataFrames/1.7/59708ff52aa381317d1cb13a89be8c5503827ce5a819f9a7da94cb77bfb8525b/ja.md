```
metadatakeys(df::AbstractDataFrame)
metadatakeys(dfr::DataFrameRow)
metadatakeys(dfc::DataFrameColumns)
metadatakeys(dfr::DataFrameRows)
```

オブジェクトに設定されているテーブルレベルのメタデータキーのイテレータを返します。

値は[`metadata(df, key)`](@ref)を使用してアクセスできます。

`SubDataFrame`および`DataFrameRow`は、親の`:note`スタイルのメタデータキーのみを公開します。

関連情報: [`metadata`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
