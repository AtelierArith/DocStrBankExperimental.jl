```
filterobs(f, data)
```

データコンテナ `data` のサブセットを返し、`f(getobs(data, i)) === true` となるすべてのインデックス `i` を含みます。

```julia
data = 1:10
numobs(data) == 10
fdata = filterobs(>(5), data)
numobs(fdata) == 5
```
