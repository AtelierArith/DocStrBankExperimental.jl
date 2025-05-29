```
serialize(cons::Construct, obj; contextkw...) -> Vector{UInt8}
serialize(T, obj; contextkw...) -> Vector{UInt8}
serialize(obj; contextkw...) -> Vector{UInt8}
```

Serialize an object in memory (a byte array).
