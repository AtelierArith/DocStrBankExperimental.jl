```
LazySets.ρ(d::AbstractVector, fp::AbstractFlowpipe)
```

### 入力

  * `d`  – 方向
  * `fp` – フローパイプ

### 出力

与えられた方向 `d` に沿ったフローパイプのサポート関数。

### 注意事項

このフォールバック実装では、フローパイプは到達集合の和のように振る舞います。すなわち、この実装は `LazySet.UnionSetArray` の実装に類似しています。
