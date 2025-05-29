```
clog(x::ZZRingElem, c::ZZRingElem)
clog(x::ZZRingElem, c::Int)
```

$$
c
$$

を底とした$x$の対数の天井を返します。

# 例

```jldoctest
julia> clog(ZZ(12), ZZ(2))
4

julia> clog(ZZ(12), 3)
3

```
