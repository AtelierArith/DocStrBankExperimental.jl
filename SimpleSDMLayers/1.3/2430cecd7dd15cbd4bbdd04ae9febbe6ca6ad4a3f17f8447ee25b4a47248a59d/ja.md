```
coarsen(f, L::SDMLayer, mask=(2, 2))
```

レイヤーを粗くするために、サイズ `mask` のサブグリッドを収集し、このマスク内のすべての非空のセルに関数 `f` を適用します。コアの制約は、`f` がベクトルを受け取り、単一の要素を返さなければならないことです（マスクのサイズはレイヤーのサイズと互換性がある必要があります）。
