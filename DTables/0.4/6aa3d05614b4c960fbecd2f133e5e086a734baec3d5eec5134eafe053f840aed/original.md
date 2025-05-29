```
groupby(d::DTable, col::Symbol; merge=true, chunksize=0) -> GDTable
```

Groups `d` by distinct values of column `col`.

The process of grouping can be affected by providing kwargs `merge` and `chunksize`. By default all the chunks belonging to a single key will be merged into a single partition. Providing a positive value in `chunksize` will attempt to merge the smaller partitions into partitions not bigger than `chunksize`. Please note that partitions bigger than `chunksize` will not be split into partitions of `chunksize`. Merging can be disabled completely by providing `merge=false`.

# Examples

```julia
julia> d = DTable((a=shuffle(repeat('a':'d', inner=4, outer=4)),), 4)
DTable with 16 partitions
Tabletype: NamedTuple

julia> DTables.groupby(d, :a)
GDTable with 4 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]

julia> DTables.groupby(d, :a, chunksize=3)
GDTable with 24 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]

julia> DTables.groupby(d, :a, merge=false)
GDTable with 42 partitions and 4 keys
Tabletype: NamedTuple
Grouped by: [:a]
```
