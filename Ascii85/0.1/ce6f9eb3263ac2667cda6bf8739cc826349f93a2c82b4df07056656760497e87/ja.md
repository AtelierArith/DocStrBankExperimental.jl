````
ascii85enc(inarr::Array{UInt8})
バイナリデータをASCII85（Adobeスタイルの<~ ~>）に変換します
# 引数
- `inarr::Array{UInt8}`: バイナリデータを持つIO
ASCII85をStringとして返します

# 例
```jldoctest
julia> a = ascii85enc(hex2bytes("123456780000000012345678abcd"))
"<~&i<X6z&i<X6X3C~>"
````
