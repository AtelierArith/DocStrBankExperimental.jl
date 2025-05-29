```
idwpars(localaniso, searcher, domain; power=2, metric=Euclidean())
```

`LocalAnisotropy` データを `searcher` から返されたローカル近傍を使用して `domain` に補間します。重みは、指定された `power` と `metric` によって逆距離加重で計算されます。カスタムキーワード引数は `interpolate` で説明されています。

## 例

```julia
searcher = KNearestSearch(data, 10)
idw3_into_grid = idwpars(localaniso, searcher, grid, power=3)
```
