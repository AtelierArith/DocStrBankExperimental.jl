```
colmetadata(df::AbstractDataFrame, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfr::DataFrameRow, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfc::DataFrameColumns, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
colmetadata(dfr::DataFrameRows, col::ColumnIndex, key::AbstractString, [default]; style::Bool=false)
```

Return column-level metadata value associated with `df` for column `col` and key `key`.

`SubDataFrame` and `DataFrameRow` expose only `:note`-style metadata of their parent.

If `default` is passed then return it if `key` does not exist for column `col`; if `style=true` return `(default, :default)`. If `col` does not exist in `df` always throw an error.

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

# Examples

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

```
