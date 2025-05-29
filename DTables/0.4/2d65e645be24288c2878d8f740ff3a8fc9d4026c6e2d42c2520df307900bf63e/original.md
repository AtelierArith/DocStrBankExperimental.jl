```
groupby(d::DTable, f::Function; merge=true, chunksize=0)
```

Groups `d` by the distinct set of keys created by applying `f` to each row in `d`.

For kwargs usage details see `groupby(d::DTable, col::Symbol)`

```julia
julia> d = DTable((a=shuffle(repeat('a':'d', inner=4, outer=4)),b=repeat(1:4, 16)), 4)
DTable with 16 partitions
Tabletype: NamedTuple

julia> function group_fun(row)
           row.a + row.b
       end
group_fun (generic function with 1 method)

julia> DTables.groupby(d, group_fun)
GDTable with 7 partitions and 7 keys
Tabletype: NamedTuple
Grouped by: group_fun

julia> DTables.groupby(d, row -> row.a + row.b, chunksize=3)
GDTable with 25 partitions and 7 keys
Tabletype: NamedTuple
Grouped by: group_fun

julia> DTables.groupby(d, row -> row.a + row.b, merge=false)
GDTable with 52 partitions and 7 keys
Tabletype: NamedTuple
Grouped by: group_fun
```
