```
AbstractDeviceArray{T, N} <: DenseArray{T, N}
```

型 `T` の `N` 次元 GPU 配列（または配列のような型）のスーパタイプ。この型のインスタンスはデバイス上に存在することが期待されます。ホスト側のオブジェクトについては [`AbstractGPUArray`](@ref) を参照してください。
