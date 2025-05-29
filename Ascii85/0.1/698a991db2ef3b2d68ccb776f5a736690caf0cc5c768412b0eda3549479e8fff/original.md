````
ascii85dec(in)
converts ASCII85 (Adobe style with <~ ~>) to binary data 
# Arguments
- `in::Array{UInt8}` or `in::String`: the ASCII85 to decode
returns the binary data as Array{UInt8}

# Examples
```jldoctest
julia> b = ascii85dec("<~&i<X6z&i<X6X3C~>")
14-element Vector{UInt8}:
0x12
0x34
0x56
0x78
0x00
0x00
0x00
0x00
0x12
0x34
0x56
0x78
0xab
0xcd
````
