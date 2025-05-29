```
BitStr{N,T} <: Integer
```

The struct for bit string with fixed length `N` and storage type `T`. It is an alias of `DitStr{2,N,T}`.

```
BitStr{N,T}(integer)
BitStr64{N}(integer)
BitStr64(vector)
LongBitStr{N}(integer)
LongBitStr(vector)
```

Returns a `BitStr`. When the input is an integer, the bits are read from right to left. When the input is a vector, the bits are read from left to right.

## Examples

`BitStr` supports some basic arithmetic operations. It acts like an integer, but supports some frequently used methods for binary basis.

```jldoctest
julia> bit"0101" * 2
1010 ₍₂₎

julia> join([bit"101" for i in 1:10])
"101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎101 ₍₂₎"

julia> repeat(bit"101", 2)
101101 ₍₂₎

julia> bit"1101"[2]
0
```
