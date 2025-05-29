```
isqrtrem(x::ZZRingElem)
```

$$
x
$$

の平方根の床$s$と余り$r$からなるタプル$s, r$を返します。すなわち、$x = s^2 + r$となるようにします。$x \geq 0$である必要があります。

# 例

```jldoctest
julia> isqrtrem(ZZ(13))
(3, 4)

```
