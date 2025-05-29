```
flog(x::ZZRingElem, c::ZZRingElem)
flog(x::ZZRingElem, c::Int)
```

$ c $ を底とした $ x $ の対数の床を返します。

# 例

```jldoctest
julia> flog(ZZ(12), ZZ(2))
3

julia> flog(ZZ(12), 3)
2

```
