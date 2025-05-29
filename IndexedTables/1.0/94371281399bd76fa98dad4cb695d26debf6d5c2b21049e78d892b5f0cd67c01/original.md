```
flatten(t::Table, col=length(columns(t)))
```

Flatten `col` column which may contain a vector of iterables while repeating the other fields. If column argument is not provided, default to last column.

# Examples:

```
x = table([1,2], [[3,4], [5,6]], names=[:x, :y])
flatten(x, 2)

t1 = table([3,4],[5,6], names=[:a,:b])
t2 = table([7,8], [9,10], names=[:a,:b])
x = table([1,2], [t1, t2], names=[:x, :y]);
flatten(x, :y)
```
