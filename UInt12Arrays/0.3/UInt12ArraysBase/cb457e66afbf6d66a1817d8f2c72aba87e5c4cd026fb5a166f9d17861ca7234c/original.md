```
UInt12Vector(data::Vector{UInt8})

The default constructor has an element type of UInt16 and is backed by a
byte (UInt8) vector that consists of packed 12-bit integers. Every three
bytes in the vector represents two 12-bit integers.

The following packing is assumed:
The 8 lower bits of the first integer are contained in the first byte.
The 4 higher bits of the first integer are first 4 bits of the second byte.
The 4 lower bits of the second integer are the last 4 bits of the second byte.
The 8 higher bits of the second integer are contained in the third byte.
```

# Example

```jldoctest
julia> A = UInt12Array(UInt8[0xba, 0xdc, 0xfe])
2-element UInt12Vector{UInt16, Vector{UInt8}}:
 0x0cba
 0x0fed

julia> A[1]
0x0cba

julia> copy(A)
2-element Vector{UInt16}:
 0x0cba
 0x0fed

julia> 
```
