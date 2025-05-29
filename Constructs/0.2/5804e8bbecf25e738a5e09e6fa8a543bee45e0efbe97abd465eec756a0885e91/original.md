```
BigEndian(T) -> Construct{T}
```

Defines the big endian format `T`.

# Examples

```jldoctest
julia> deserialize(BigEndian(UInt16), b"\x12\x34")
0x1234
```
