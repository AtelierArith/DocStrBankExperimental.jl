```
unsafe_free!(a::GPUArray)
```

配列のメモリを再利用のために解放します。この操作は、配列がスコープ外になるときにGCによって自動的に実行されますが、メモリアロケータへの負荷を軽減するために早めに呼び出すこともできます。
