```
rowsmin(zep::Zeppelin, col::Symbol; n::Int=10000000, classname::Union{Missing,AbstractString}=missing)
```

Returns the row indices associated with the `n` minimum values in the `col` column.

Examples:

```
# Plot ten smallest by :DAVG
plot(zep, rowsmin(zep, :DAVG, 10))
# data from 100 most Iron-rich sorted by DAVG
rowsmin(DataFrame, zep, rowsmax(zep, :FE, 100), sortCol=:DAVG)
```
