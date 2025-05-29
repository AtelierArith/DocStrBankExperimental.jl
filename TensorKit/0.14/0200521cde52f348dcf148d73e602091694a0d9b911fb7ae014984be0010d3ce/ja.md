```
AbstractTensor{T,S,N} = AbstractTensorMap{T,S,N,0}
```

すべてのテンソルの抽象スーパタイプ、すなわち型 `ProductSpace{S, N}` のテンソル積空間の要素で、要素型 `T` を持ちます。

`AbstractTensor{T, S, N}` は実際には特別なケースであり、`AbstractTensorMap{T, S, N, 0}` です。すなわち、非自明な出力空間のみを持つテンソルマップです。
