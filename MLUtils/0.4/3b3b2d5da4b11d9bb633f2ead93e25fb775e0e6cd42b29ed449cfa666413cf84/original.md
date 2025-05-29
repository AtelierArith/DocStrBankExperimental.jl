```
joinobs(datas...)
```

Concatenate data containers `datas`.

```julia
data1, data2 = 1:10, 11:20
jdata = joinumobs(data1, data2)
getobs(jdata, 15) == 15
```
