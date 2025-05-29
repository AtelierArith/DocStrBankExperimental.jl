```
nlevstbl(nm::Symbol, n, vars::Pair{Symbol, Vector{String}}...)
```

Return a `Tables.columntable` with a `nm` column as a `PooledArray` with `n` levels.

If any `vars` pairs are given they are expanded to columns representing characteristics of the `nm` column.  In experimental design terminology, if say `nm` is `:item` then these represent between-item experimental factors.

The `nm` column is generated as `nlevels(n, uppercase(first(string(nm))))`

# Examples

```julia-repl
julia> nlevstbl(:item, 10)
(item = ["I01", "I02", "I03", "I04", "I05", "I06", "I07", "I08", "I09", "I10"],)

julia> nlevstbl(:item, 9, :level => ["low", "medium", "high"])
(item = ["I1", "I2", "I3", "I4", "I5", "I6", "I7", "I8", "I9"], level = ["low", "medium", "high", "low", "medium", "high", "low", "medium", "high"])
```
