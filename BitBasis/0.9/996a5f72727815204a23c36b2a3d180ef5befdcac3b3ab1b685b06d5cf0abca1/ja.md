```
BitStr{N,T} <: Integer
```

固定長 `N` とストレージタイプ `T` を持つビット文字列の構造体です。これは `DitStr{2,N,T}` のエイリアスです。

```
BitStr{N,T}(integer)
BitStr64{N}(integer)
BitStr64(vector)
LongBitStr{N}(integer)
LongBitStr(vector)
```

`BitStr` を返します。入力が整数の場合、ビットは右から左に読み取られます。入力がベクトルの場合、ビットは左から右に読み取られます。

## 例

`BitStr` はいくつかの基本的な算術演算をサポートしています。整数のように振る舞いますが、二進法の基礎に対してよく使われるいくつかのメソッドをサポートしています。

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
