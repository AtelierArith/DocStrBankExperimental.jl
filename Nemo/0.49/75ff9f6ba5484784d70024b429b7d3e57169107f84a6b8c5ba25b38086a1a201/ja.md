```
isqrtrem(x::ZZRingElem)
```

タプル $s, r$ を返します。ここで $s$ は $x$ の平方根の床、$r$ は余りです。すなわち、$x = s^2 + r$ となります。$x \geq 0$ である必要があります。

# 例

```jldoctest
julia> isqrtrem(ZZ(13))
(3, 4)

```
