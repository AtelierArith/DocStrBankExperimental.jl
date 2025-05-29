```
pkeys(itr::IndexedTable)
```

Primary keys of the table. If Table doesn't have any designated primary key columns (constructed without `pkey` argument) then a default key of tuples `(1,):(n,)` is generated.

# Example

```
a = table(["a","b"], [3,4]) # no pkey
pkeys(a)

a = table(["a","b"], [3,4], pkey=1)
pkeys(a)
```
