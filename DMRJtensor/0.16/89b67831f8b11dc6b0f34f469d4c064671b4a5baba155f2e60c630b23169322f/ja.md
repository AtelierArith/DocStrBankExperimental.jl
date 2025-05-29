Omat(m)

サイズ `m x m` のゼロのための予約された文字列 "O" を持つバルク行列積演算子を生成します。このオブジェクトを掛けることで、特定のシステムのためのバルクMPOを得ることができます。

# 例:

```julia

H = bulkMPO(5) #["O" for i = 1:5,j = 1:5]

#XXZモデル
H[1,1] = H[end,end] = "I"
H[2,1] = "S"*Char(0x207B)
H[3,1] = "S"*Char(0x207A)
H[4,1] = "Sz"
H[end,2] = half*"S"*Char(0x207A)
H[end,3] = half*"S"*Char(0x207B)
H[end,4] = "Sz"
H*H*H #3つのサイトを掛け合わせる

```

参照: [`bulkMPO`](@ref) [`half`](@ref)
