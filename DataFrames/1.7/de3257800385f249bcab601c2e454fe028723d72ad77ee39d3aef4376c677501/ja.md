```
metadata(df::AbstractDataFrame, key::AbstractString, [default]; style::Bool=false)
metadata(dfr::DataFrameRow, key::AbstractString, [default]; style::Bool=false)
metadata(dfc::DataFrameColumns, key::AbstractString, [default]; style::Bool=false)
metadata(dfr::DataFrameRows, key::AbstractString, [default]; style::Bool=false)
```

`df` に関連付けられたキー `key` のテーブルレベルのメタデータ値を返します。`style=true` の場合、メタデータ値とメタデータスタイルのタプルを返します。

`SubDataFrame` と `DataFrameRow` は親の `:note` スタイルのメタデータのみを公開します。

`default` が渡された場合、`key` が存在しないときにそれを返します。`style=true` の場合は `(default, :default)` を返します。

参照: [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
