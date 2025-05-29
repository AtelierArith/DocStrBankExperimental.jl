```
clrbit!(x::ZZRingElem, c::Int)
```

$$
x
$$

の$c$ビットをクリアします。最も下位のビットは$0$-thビットです。この関数は入力をインプレースで変更します。

# 例

```jldoctest
julia> a = ZZ(12)
12

julia> clrbit!(a, 3)

julia> a
4
```
