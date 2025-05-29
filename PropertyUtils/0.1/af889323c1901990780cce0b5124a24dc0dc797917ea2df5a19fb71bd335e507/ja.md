```
indexes(x)
```

`getproperty`を`getindex`にマップします。

# 例

```
d = Dict(:x => 1, :y => 2)
id = indexes(d)
id.x
id.z = 3
```
