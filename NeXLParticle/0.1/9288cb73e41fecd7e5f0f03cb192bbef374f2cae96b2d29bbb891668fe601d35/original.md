```
rowsclass(zep::Zeppelin, classname::AbstractString; shuffle=false, n=1000000)
```

Returns the row indices associated with the specified `classname`.  If `shuffle` is true, the row indices are shuffled so that a randomized n can be plucked off to plot or other.

Example:

```
# Plot a randomized selection of 10 "Calcite" particles
plot(zep, rowsclass(zep, "Calcite", shuffle=true, n=10), xmax=8.0e3)
```
