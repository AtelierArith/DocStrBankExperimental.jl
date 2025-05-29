```
transform(t::Table, changes::Pair...)
```

Transform columns of `t`. For each pair `col => value` in `changes` the column `col` is replaced by the `AbstractVector` `value`. If `col` is not an existing column, a new column is created.

# Examples:

```
t = table([1,2], [3,4], names=[:x, :y])

# change second column to [5,6]
transform(t, 2 => [5,6])
transform(t, :y => :y => x -> x + 2)

# add [5,6] as column :z
transform(t, :z => 5:6)
transform(t, :z => :y => x -> x + 2)

# replacing the primary key results in a re-sorted copy
t = table([0.01, 0.05], [1,2], [3,4], names=[:t, :x, :y], pkey=:t)
t2 = transform(t, :t => [0.1,0.05])

# the column :z is not part of t so a new column is added
t = table([0.01, 0.05], [2,1], [3,4], names=[:t, :x, :y], pkey=:t)
transform(t, :z => [1//2, 3//4])
```
