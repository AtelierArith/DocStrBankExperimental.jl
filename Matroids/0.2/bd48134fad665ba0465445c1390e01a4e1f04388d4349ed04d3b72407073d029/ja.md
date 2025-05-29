```
add!(g::EasyMultiGraph, u, v)
add!(g::EasyMultiGraph, (u,v))
```

多重グラフにエッジを追加し、その重複度を1増やします。成功した場合は`true`を返します。
