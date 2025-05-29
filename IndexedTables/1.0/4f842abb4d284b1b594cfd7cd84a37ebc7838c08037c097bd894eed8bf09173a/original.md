```
rename(t, map::Pair...)
```

For each pair `col => newname` in `map`, set `newname` as the new name for column `col` in `t`. Returns a new table.

# Example

```
t = table([0.01, 0.05], [2,1], names=[:t, :x])
rename(t, :t => :time)
```
