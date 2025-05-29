```
unstack(t, by = pkeynames(t); variable = :variable, value = :value)
```

Reshape a table from the long to the wide format. Columns in `by` are kept as indexing columns. Keyword arguments `variable` and `value` denote which column contains the column identifier and which the corresponding values.  See also [`stack`](@ref).

# Examples

```
t = table(1:4, [1, 4, 9, 16], [1, 8, 27, 64], names = [:x, :xsquare, :xcube], pkey = :x);

long = stack(t)

unstack(long)
```
