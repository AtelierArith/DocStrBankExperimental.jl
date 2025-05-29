```
insertcolsafter(t, after, map::Pair...)
```

For each pair `name => col` in `map`, insert a column `col` named `name` after `after`. Returns a new table.

# Example

```
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
insertcolsafter(t, :t, :w => [0,1])
```
