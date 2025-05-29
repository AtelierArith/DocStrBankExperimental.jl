```
groupobs(f, data)
```

データコンテナ `data` を `f(obs)` によって観測値をグループ化して異なるデータコンテナに分割します。

```julia
data = -10:10
datas = groupobs(>(0), data)
length(datas) == 2
```
