````
ascii85enc(inarr::Array{UInt8})
converts binary data to ASCII85 (Adobe style with <~ ~>)
# Arguments
- `inarr::Array{UInt8}`: an IO with binary data
returns ASCII85 as String

# Examples
```jldoctest
julia> a = ascii85enc(hex2bytes("123456780000000012345678abcd"))
"<~&i<X6z&i<X6X3C~>"
````
