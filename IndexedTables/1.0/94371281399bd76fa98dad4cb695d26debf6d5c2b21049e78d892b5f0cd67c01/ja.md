```
flatten(t::Table, col=length(columns(t)))
```

`col` 列をフラット化します。この列には反復可能なベクターが含まれている可能性があり、他のフィールドは繰り返されます。列引数が指定されていない場合、デフォルトで最後の列になります。

# 例:

```
x = table([1,2], [[3,4], [5,6]], names=[:x, :y])
flatten(x, 2)

t1 = table([3,4],[5,6], names=[:a,:b])
t2 = table([7,8], [9,10], names=[:a,:b])
x = table([1,2], [t1, t2], names=[:x, :y]);
flatten(x, :y)
```
