```
coordinates(@nospecialize(ids::IDS), field::Symbol; coord_leaves::Union{Nothing,Vector{<:Union{Nothing,Symbol}}}=nothing)
```

Return two lists, one of coordinate names and the other with their values in the data structure

Coordinate value is `nothing` when the data does not have a coordinate

Coordinate value is `missing` if the coordinate is missing in the data structure

Use `coord_leaves` to override fetching coordinates of a given field
