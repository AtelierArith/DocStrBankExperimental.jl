```
CuPtr{T}
```

GPUからアクセス可能な型`T`のデータを指すメモリアドレスです。`CuPtr`は通常の`Ptr`オブジェクトとABI互換性があり、例えばGPUメモリへの`Ptr`を期待する関数を`ccall`するために使用できますが、両者の間での誤った変換を防ぎます。
