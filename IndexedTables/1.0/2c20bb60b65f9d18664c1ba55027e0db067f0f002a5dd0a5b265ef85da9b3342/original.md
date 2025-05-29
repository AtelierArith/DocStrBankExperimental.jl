```
Keys()
```

Select the primary keys.

# Examples

```
t = table([1,1,2,2], [1,2,1,2], [1,2,3,4], names=[:a,:b,:c], pkey = (:a, :b))
select(t, Keys())
```
