```
groupby(d::DTable, cols::Vector{Symbol}; merge=true, chunksize=0)
```

Groups the `d` by distinct values of columns `cols`. The key is constructed by creating a NamedTuple from each row based on `cols` provided.

For kwargs usage details see `groupby(d::DTable, col::Symbol)`

# Examples

```julia
julia> d = DTable((a=shuffle(repeat('a':'d', inner=4, outer=4)),b=repeat(1:4, 16)), 4)
DTable with 16 partitions
Tabletype: NamedTuple

julia> DTables.groupby(d, [:a,:b])
GDTable with 16 partitions and 16 keys
Tabletype: NamedTuple
Grouped by: [:a, :b]

julia> DTables.groupby(d, [:a,:b], chunksize=3)
GDTable with 27 partitions and 16 keys
Tabletype: NamedTuple
Grouped by: [:a, :b]

julia> DTables.groupby(d, [:a,:b], merge=false)
GDTable with 64 partitions and 16 keys
Tabletype: NamedTuple
Grouped by: [:a, :b]
```
