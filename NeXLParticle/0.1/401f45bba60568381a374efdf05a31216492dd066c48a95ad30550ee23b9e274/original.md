```
rowsmax(zep::Zeppelin, col::Symbol; n::Int=10000000, classname::Union{Missing,AbstractString}=missing)
```

Returns the row indices associated with the `n` maximum values in the `col` column.

Examples:

```
# Plot ten largest by :DAVG
plot(zep, rowsmax(zep, :DAVG, 10))
# data from 100 most Iron-rich sorted by DAVG
rowsmax(DataFrame, zep, rowsmax(zep, :FE, 100), sortCol=:DAVG)
```
