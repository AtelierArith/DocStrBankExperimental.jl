```
tstbit(x::ZZRingElem, c::Int)
```

xのビット$i$を返します（0から番号付け）。1の場合は`true`、0の場合は`false`です。

# 例

```jldoctest
julia> a = ZZ(12)
12

julia> tstbit(a, 0)
false

julia> tstbit(a, 2)
true
```
