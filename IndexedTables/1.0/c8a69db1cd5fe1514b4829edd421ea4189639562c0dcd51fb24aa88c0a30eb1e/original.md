```
select(t::Table, which::Selection)
```

Select all or a subset of columns, or a single column from the table.

`Selection` is a type union of many types that can select from a table. It can be:

1. `Integer` – returns the column at this position.
2. `Symbol` – returns the column with this name.
3. `Pair{Selection => Function}` – selects and maps a function over the selection, returns the result.
4. `AbstractArray` – returns the array itself. This must be the same length as the table.
5. `Tuple` of `Selection` – returns a table containing a column for every selector in the tuple.
6. `Regex` – returns the columns with names that match the regular expression.
7. `Type` – returns columns with elements of the given type.

# Examples:

```
t = table(1:10, randn(10), rand(Bool, 10); names = [:x, :y, :z])

# select the :x vector
select(t, 1)
select(t, :x)

# map a function to the :y vector
select(t, 2 => abs)
select(t, :y => x -> x > 0 ? x : -x)

# select the table of :x and :z
select(t, (:x, :z))
select(t, r"(x|z)")

# map a function to the table of :x and :y
select(t, (:x, :y) => row -> row[1] + row[2])
select(t, (1, :y) => row -> row.x + row.y)
```
