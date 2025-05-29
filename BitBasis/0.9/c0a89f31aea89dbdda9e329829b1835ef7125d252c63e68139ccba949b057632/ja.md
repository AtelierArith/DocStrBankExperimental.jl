```
DitStr{D,N,T<:Integer} <: Integer
```

固定長 `N` とストレージタイプ `T` を持つディット文字列の構造体で、ここで `dit` は2進数システムからd進数システムへの拡張です。

```
DitStr{D,N,T}(integer)
DitStr{D,N}(integer)
DitStr{D}(vector)
```

`DitStr` を返します。入力が整数の場合、ディットは右から左に読み取られます。入力がベクトルの場合、ディットは左から右に読み取られます。

### 例

```jldoctest
julia> DitStr{3}([1,2,1,1,0])
01121 ₍₃₎

julia> DitStr{3, 5}(71)
02122 ₍₃₎
```
