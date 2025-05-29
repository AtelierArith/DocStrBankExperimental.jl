```
mapobs(namedfs::NamedTuple, data)
```

`NamedTuple` の関数を `data` に適用し、`NamedTuple` のデータコンテナに変換します。フィールド構文を使用して、結果のデータコンテナの列を選択できます。

```julia
data = 1:10
nameddata = mapobs((x = sqrt, y = log), data)
getobs(nameddata, 10) == (x = sqrt(10), y = log(10))
getobs(nameddata.x, 10) == sqrt(10)
```
