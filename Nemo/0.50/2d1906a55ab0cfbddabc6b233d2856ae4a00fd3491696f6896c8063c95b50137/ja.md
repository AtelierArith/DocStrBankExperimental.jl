```
combit!(x::ZZRingElem, c::Int)
```

$$
x
$$

の$c$ビットを補完します。最下位ビットは$0$-thビットです。この関数は入力をその場で変更します。

# 例

```jldoctest
julia> a = ZZ(12)
12

julia> combit!(a, 2)

julia> a
8
```
