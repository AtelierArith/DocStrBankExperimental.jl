```
indexes(x)
```

Map `getproperty` to `getindex`.

# Example

```
d = Dict(:x => 1, :y => 2)
id = indexes(d)
id.x
id.z = 3
```
