```
deletecolmetadata!(df::AbstractDataFrame, col::ColumnIndex, key::AbstractString)
deletecolmetadata!(dfr::DataFrameRow, col::ColumnIndex, key::AbstractString)
deletecolmetadata!(dfc::DataFrameColumns, col::ColumnIndex, key::AbstractString)
deletecolmetadata!(dfr::DataFrameRows, col::ColumnIndex, key::AbstractString)
```

Delete column-level metadata set in `df` for column `col` and key `key` and return `df`.

For `SubDataFrame` and `DataFrameRow` only `:note`-style metadata from their parent can be deleted (as other styles are not propagated to views).

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`colmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
