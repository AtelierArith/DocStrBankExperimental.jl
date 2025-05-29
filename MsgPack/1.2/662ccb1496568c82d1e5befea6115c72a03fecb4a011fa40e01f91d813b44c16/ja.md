```
pack(x)
```

`x`をMessagePack形式にシリアライズし、結果の`Vector{UInt8}`を返します。

この関数は、[`msgpack_type`](@ref)と[`to_msgpack`](@ref)を使用して、`value`をMessagePack形式に適切に変換します。

参照: [`unpack`](@ref)
