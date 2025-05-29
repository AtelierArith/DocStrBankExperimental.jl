````
ascii85dec(in)
ASCII85（Adobeスタイルの<~ ~>）をバイナリデータに変換します
# 引数
- `in::Array{UInt8}` または `in::String`: デコードするASCII85
バイナリデータをArray{UInt8}として返します

# 例
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
