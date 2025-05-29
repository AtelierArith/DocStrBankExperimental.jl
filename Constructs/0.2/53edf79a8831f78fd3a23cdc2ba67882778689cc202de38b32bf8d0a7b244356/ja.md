```
serialize(cons::Construct, obj; contextkw...) -> Vector{UInt8}
serialize(T, obj; contextkw...) -> Vector{UInt8}
serialize(obj; contextkw...) -> Vector{UInt8}
```

メモリ内のオブジェクトをシリアライズします（バイト配列）。
