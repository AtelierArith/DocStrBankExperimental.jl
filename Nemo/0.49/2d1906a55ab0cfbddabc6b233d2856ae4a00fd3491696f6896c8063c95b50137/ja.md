```
combit!(x::ZZRingElem, c::Int)
```

$$
x
$$

の補完ビット$c$を変更します。最下位ビットは$0$-thビットです。この関数は入力をその場で変更します。

# 例

```jldoctest
julia> a = ZZ(12)
12

julia> combit!(a, 2)

julia> a
8
```
