```
groupobs(f, data)
```

Split data container data `data` into different data containers, grouping observations by `f(obs)`.

```julia
data = -10:10
datas = groupobs(>(0), data)
length(datas) == 2
```
