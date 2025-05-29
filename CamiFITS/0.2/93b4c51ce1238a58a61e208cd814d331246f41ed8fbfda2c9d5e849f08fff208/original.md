```
fits_remove_zero_offset(data)
```

Shift the `Int` range of values onto the `UInt` range by *adding* to the `data` the appropriate integer offset value as specified by the `BZERO` keyword.

NB. Since the FITS format *does not support a native unsigned integer data  type* (except `UInt8`), unsigned values of the types `UInt16`, `UInt32` and  `UInt64`, are recovered from stored native signed integers of the types `Int16`, `Int32` and `Int64`, respectively, by *adding* the appropriate integer offset  specified by the (positive) `BZERO` keyword value. For the byte data type  (`UInt8`), the converse technique can be used to recover the signed byte values (`Int8`) from the stored native unsigned values (`UInt`) by *adding* the  (negative) `BZERO` offset value. 

This method is included and used in *reading* stored data to ensure backward  compatibility with software not supporting native values of the types  `Int8`, `UInt16`, `UInt32` and `UInt64`.

#### Example:

```
julia> fits_remove_zero_offset(Int32[-2147483648])
1-element Vector{UInt32}:
 0x00000000

julia> Int(0x00000000)
0

julia> fits_remove_zero_offset(UInt8[128])
1-element Vector{Int8}:
 0
```
