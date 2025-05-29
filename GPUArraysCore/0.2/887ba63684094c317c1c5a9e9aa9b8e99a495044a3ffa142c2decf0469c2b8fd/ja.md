```
AbstractGPUArray{T, N} <: DenseArray{T, N}
```

型 `T` の要素を持つ `N` 次元 GPU 配列（または配列のような型）のスーパタイプ。この型のインスタンスはホスト上に存在することが期待されており、デバイス側のオブジェクトについては [`AbstractDeviceArray`](@ref) を参照してください。
