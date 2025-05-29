```
SnpArray
SnpArray(bednm, m)
SnpArray(plknm)
SnpArray(undef, m, n)
```

Raw .bed file as a shared, memory-mapped Matrix{UInt8}.  The number of rows, `m` is stored separately because it is not uniquely determined by the size of the `data` field.
