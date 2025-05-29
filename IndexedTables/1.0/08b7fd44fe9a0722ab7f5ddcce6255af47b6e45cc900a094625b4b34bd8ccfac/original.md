```
pkeynames(t::Table)
```

Names of the primary key columns in `t`.

# Examples

```
t = table([1,2], [3,4]);
pkeynames(t)

t = table([1,2], [3,4], pkey=1);
pkeynames(t)

t = table([2,1],[1,3],[4,5], names=[:x,:y,:z], pkey=(1,2));
pkeynames(t)
```
