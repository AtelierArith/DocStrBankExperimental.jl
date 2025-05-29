```
stack(t, by = pkeynames(t); select = Not(by), variable = :variable, value = :value)`
```

Reshape a table from the wide to the long format. Columns in `by` are kept as indexing columns. Columns in `select` are stacked. In addition to the id columns, two additional columns labeled `variable` and `value` are added, containing the column identifier and the stacked columns. See also [`unstack`](@ref).

# Examples

```
t = table(1:4, names = [:x], pkey=:x)
t = pushcol(t, :xsquare, :x => x -> x^2)
t = pushcol(t, :xcube  , :x => x -> x^3)

stack(t)
```
