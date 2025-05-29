```
reindex(t::IndexedTable, by)
reindex(t::IndexedTable, by, select)
```

Reindex table `t` with new primary key `by`, optionally keeping a subset of columns via `select`.  For [`NDSparse`](@ref), use [`selectkeys`](@ref).

# Example

```
t = table([2,1],[1,3],[4,5], names=[:x,:y,:z], pkey=(1,2))

t2 = reindex(t, (:y, :z))

pkeynames(t2)
```
