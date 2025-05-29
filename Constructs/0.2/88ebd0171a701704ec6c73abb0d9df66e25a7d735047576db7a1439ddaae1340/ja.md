```
LittleEndian(T) -> Construct{T}
```

リトルエンディアン形式 `T` を定義します。

# 例

```jldoctest
julia> deserialize(LittleEndian(UInt16), b"\x12\x34")
0x3412
```
