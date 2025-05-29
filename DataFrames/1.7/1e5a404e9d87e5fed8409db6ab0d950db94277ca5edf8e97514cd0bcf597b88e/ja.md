```
colmetadata(df::AbstractDataFrame, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfr::DataFrameRow, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfc::DataFrameColumns, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfr::DataFrameRows, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
```

`df`の列`col`に関連付けられたメタデータ値を返します。キーは`key`です。

`SubDataFrame`と`DataFrameRow`は親の`:note`スタイルのメタデータのみを公開します。

`default`が渡された場合、`key`が列`col`に存在しない場合はそれを返します。`style=true`の場合は`(default, :default)`を返します。`col`が`df`に存在しない場合は常にエラーをスローします。

参照: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref)。

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
