```
smoothpars(localaniso, searcher; b=0.0, kwargs)
smoothpars(localaniso, searcher, domain; b=0.0, kwargs)
```

`LocalAnisotropy`をスムーズにし、`searcher`から返されたローカル近傍を使用します。`b` = 0の場合は単純なローカル平均、それ以外の場合は指定されたバンド幅でのガウスカーネルスムージングです。カスタムkwargsは`interpolate`で説明されています。

## 例

```julia
searcher = KNearestSearch(data, 10)
averaged_inplace = smoothpars(localaniso, searcher)
averaged_grid = smoothpars(localaniso, searcher, grid, b=0.6)
```
