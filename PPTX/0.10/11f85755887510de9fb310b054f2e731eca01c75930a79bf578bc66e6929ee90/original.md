```julia
Table(;
    content,
    offset_x::Real = 50,
    offset_y::Real = 50,
    size_x::Real = 150,
    size_y::Real = 100,
    column_widths::Vector{<:Real}, # set size per column
    row_heights::Vector{<:Real}, # set size per row
    header::Bool = true, # whether to automatically write the columnnames as headers
    bandrow::Bool = true, # whether to use alternating coloring per row
)
```

A Table to be used on a Slide.

The content can be anything that adheres to a `Tables.jl` interface.

Offsets and sizes are in millimeters, but will be converted to EMU.

To style each cell individually see `TableCell`.

# Examples

```jldoctest
julia> using PPTX, DataFrames

julia> df = DataFrame(a = [1,2], b = [3,4], c = [5,6])
2×3 DataFrame
 Row │ a      b      c     
     │ Int64  Int64  Int64 
─────┼─────────────────────
   1 │     1      3      5
   2 │     2      4      6

julia> t = Table(content=df, size_x=30)
Table
 content isa DataFrames.DataFrame
 offset_x is 1800000 EMUs
 offset_y is 1800000 EMUs
 size_x is 1080000 EMUs
 size_y is 3600000 EMUs

```
