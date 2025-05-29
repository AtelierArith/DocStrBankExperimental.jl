```
colmetadata!(df::AbstractDataFrame, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfr::DataFrameRow, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfc::DataFrameColumns, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
colmetadata!(dfr::DataFrameRows, col::ColumnIndex, key::AbstractString, value; style::Symbol=:default)
```

Set column-level metadata in `df` for column `col` and key `key` to have value `value` and style `style` (`:default` by default) and return `df`.

For `SubDataFrame` and `DataFrameRow` only `:note` style is allowed. Trying to set a key-value pair for which the key already exists in the parent data frame with another style throws an error.

See also: [`metadata`](@ref), [`metadatakeys`](@ref), [`metadata!`](@ref), [`deletemetadata!`](@ref), [`emptymetadata!`](@ref), [`colmetadata`](@ref), [`colmetadatakeys`](@ref), [`deletecolmetadata!`](@ref), [`emptycolmetadata!`](@ref).

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
