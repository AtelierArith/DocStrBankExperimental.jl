n量子ビットのGHZ状態を準備します。

```jldoctest
julia> ghz()
+ XXX
+ ZZ_
+ _ZZ

julia> ghz(2)
+ XX
+ ZZ

julia> ghz(4)
+ XXXX
+ ZZ__
+ _ZZ_
+ __ZZ
```
