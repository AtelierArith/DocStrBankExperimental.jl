```
@construct [ConstructName] structdefinition
```

Generate a [`Construct`](@ref) subtype with `ConstructName` for the given `struct`.

# Examples

```jldoctest
julia> @construct struct Bitmap
           ::Const(b"BMP")
           width::UInt16le
           height::UInt16le
           pixel::SizedArray(UInt8, this.height, this.width)
       end

julia> deserialize(Bitmap, b"BMP\x03\x00\x02\x00\x01\x02\x03\x04\x05\x06")
Bitmap(0x0003, 0x0002, UInt8[0x01 0x03 0x05; 0x02 0x04 0x06])

julia> serialize(Bitmap(2, 3, UInt8[1 2; 4 6; 8 9]))
13-element Vector{UInt8}:
 0x42
 0x4d
 0x50
 0x02
 0x00
 0x03
 0x00
 0x01
 0x04
 0x08
 0x02
 0x06
 0x09

julia> estimatesize(Bitmap)
UnboundedSize(0x0000000000000007)
```
