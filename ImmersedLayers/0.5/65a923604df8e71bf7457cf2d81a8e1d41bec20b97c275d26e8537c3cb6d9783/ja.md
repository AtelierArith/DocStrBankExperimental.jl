```
ones_gridgrad(::BasicILMCache,dim)
```

キャッシュ内のグリッドデータの勾配のインスタンスを取得し、方向 `dim` に沿って値を1に設定します。データが `TensorGridData` 型の場合、`dim` は1から2^2の値を取ります。
