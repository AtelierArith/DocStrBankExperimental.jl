```
pseudoabsencemask(::Type{RandomSelection}, presences::SDMLayer{Bool})
```

ランダム選択法を使用して擬似欠損のマスクを生成します。擬似欠損マスクの候補セルは、(i) *レイヤー* のバウンディングボックス内にあり（存在のバウンディングボックスを使用するには `SurfaceRangeEnvelope` を使用）、(ii) レイヤー内で値が設定されています。
