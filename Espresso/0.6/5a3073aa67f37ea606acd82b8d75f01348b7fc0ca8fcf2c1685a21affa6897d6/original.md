Split possibly indexed variable into a name and indices. Examples:

```
split_indexed(:x)         ==> (:x, [])
split_indexed(:(x[i,j]))  ==> (:x, [:i,:j])
```

See also: make_indexed
