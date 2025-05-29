```
deserialize(cons::Construct{T}, bytes::AbstractVector{UInt8}; contextkw...) -> T
deserialize(T, bytes::AbstractVector{UInt8}; contextkw...) -> T
```

バイト配列をオブジェクトにデシリアライズします。
