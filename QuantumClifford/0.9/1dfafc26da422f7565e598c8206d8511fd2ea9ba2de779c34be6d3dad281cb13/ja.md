2つのパウリ演算子の積の位相を取得します。

位相は、UInt8の低い量子ビットにF(4)としてエンコードされています。

```jldoctest
julia> P"ZZZ"*P"XXX"
-iYYY

julia> prodphase(P"ZZZ", P"XXX")
0x03

julia> prodphase(P"XXX", P"ZZZ")
0x01
```
