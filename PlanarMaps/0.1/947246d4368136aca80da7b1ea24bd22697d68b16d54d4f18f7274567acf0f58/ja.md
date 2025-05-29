```
allwoods(P::PlanarMap,C::Channel)
```

平面マップ `P` のすべての `WoodedTriangulation` のシーケンスをチャネル `C` に送信します。

# 例:

```julia
# サイズ10のランダムにサンプリングされた木付き三角形分割の
# シュナイダー木の数をカウントする
sum(1 for W in Channel(C->allwoods(PlanarMap(UWT(10)),C)))
```
