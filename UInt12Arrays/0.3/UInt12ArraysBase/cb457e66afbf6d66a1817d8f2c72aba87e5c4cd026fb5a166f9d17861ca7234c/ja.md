```
UInt12Vector(data::Vector{UInt8})

デフォルトコンストラクタは要素型がUInt16で、12ビット整数がパックされたバイト（UInt8）ベクターによってサポートされています。ベクター内の3バイトごとに2つの12ビット整数が表されます。

次のパッキングが仮定されています：
最初の整数の下位8ビットは最初のバイトに含まれています。
最初の整数の上位4ビットは2番目のバイトの最初の4ビットです。
2番目の整数の下位4ビットは2番目のバイトの最後の4ビットです。
2番目の整数の上位8ビットは3番目のバイトに含まれています。
```

# 例

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
