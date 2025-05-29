```julia
B = signed_exponent(A::AbstractArray{T}) where {T<:Base.IEEEFloat}
```

Float16、Float32、または Float64 配列の指数ビットを IEEE 標準のバイアス形式から符号-大きさ表現に変換します。

# 例

```julia
julia> bitstring(10f0,:split)
"0 10000010 01000000000000000000000"

julia> bitstring.(signed_exponent([10f0]),:split)[1]
"0 00000011 01000000000000000000000"
```

IEEE 標準の浮動小数点数では、指数 3 は 0b10000010=130 から Float32 の指数バイアス 127 を引くことで解釈されます。符号-大きさ表現では、指数は最初の指数 (0) を符号ビットとして、2^1 + 2^1 = 3 の大きさとして推測されます。NaN/Inf の指数ビットは符号-大きさ表現で負のゼロにマッピングされ、これは `biased_exponent` で正確に逆になります。
