```
LittleEndian(T) -> Construct{T}
```

Defines the little endian format `T`.

# Examples

```jldoctest
julia> deserialize(LittleEndian(UInt16), b"\x12\x34")
0x3412
```
