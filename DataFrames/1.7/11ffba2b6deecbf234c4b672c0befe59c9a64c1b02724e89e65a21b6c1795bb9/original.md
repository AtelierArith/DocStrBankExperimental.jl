```
colmetadatakeys(df::AbstractDataFrame, [col::ColumnIndex])
colmetadatakeys(dfr::DataFrameRow, [col::ColumnIndex])
colmetadatakeys(dfc::DataFrameColumns, [col::ColumnIndex])
colmetadatakeys(dfr::DataFrameRows, [col::ColumnIndex])
```

If `col` is passed return an iterator of column-level metadata keys which are set for column `col`. If `col` is not passed return an iterator of `col => colmetadatakeys(x, col)` pairs for all columns that have metadata, where `col` are `Symbol`.

Values can be accessed using [`colmetadata(df, col, key)`](@ref).

`SubDataFrame` and `DataFrameRow` expose only `:note`-style metadata of their parent.

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadata!`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
