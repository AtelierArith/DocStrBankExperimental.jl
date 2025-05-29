```
spzeros(T::Type, W::TensorMapSumSpace)
spzeros(T, W, nonzero_inds)
```

型 `T` と空間 `W` に互換性のあるスパースブロックテンソルを構築します。デフォルトでは、テンソルは空ですが、非ゼロエントリはインデックスのタプル `nonzero_inds` を渡すことで指定できます。
