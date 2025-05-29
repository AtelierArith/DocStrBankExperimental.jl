```
insertcols(t, position::Integer, map::Pair...)
```

For each pair `name => col` in `map`, insert a column `col` named `name` starting at `position`. Returns a new table.

# Example

```
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
insertcol(t, 2, :w => [0,1])
```
