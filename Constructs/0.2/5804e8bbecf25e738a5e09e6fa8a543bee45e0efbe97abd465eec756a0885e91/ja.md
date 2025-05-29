```
BigEndian(T) -> Construct{T}
```

ビッグエンディアン形式 `T` を定義します。

# 例

```jldoctest
julia> deserialize(BigEndian(UInt16), b"\x12\x34")
0x1234
```
