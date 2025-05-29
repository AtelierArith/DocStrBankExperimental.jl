```
fits_apply_zero_offset(data)
```

Shift the `UInt` range of values onto the `Int` range by *substracting* from  the `data` the appropriate integer offset value as specified by the `BZERO`  keyword.

NB. Since the FITS format *does not support a native unsigned integer data  type* (except `UInt8`), unsigned values of the types `UInt16`, `UInt32` and  `UInt64`, are stored as native signed integers of the types `Int16`, `Int32`  and `Int64`, respectively, after *substracting* the appropriate integer offset  specified by the (positive) `BZERO` keyword value. For the byte data type  (`UInt8`), the converse technique can be used to store signed byte values  (`Int8`) as native unsigned values (`UInt`) after subtracting the (negative)  `BZERO` offset value. 

This method is included and used in storing of data to ensure backward  compatibility with software not supporting native values of the types `Int8`,  `UInt16`, `UInt32` and `UInt64`.

#### Example:

```
julia> fits_apply_zero_offset(UInt32[0])
1-element Vector{Int32}:
 -2147483648

julia> fits_apply_zero_offset(Int8[0])
1-element Vector{UInt8}:
 0x80

julia> Int(0x80)
128
```
