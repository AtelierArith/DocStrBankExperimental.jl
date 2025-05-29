```
iroot(x::ZZRingElem, n::Int)
```

$$
x
$$

の$n$-乗根の整数切り捨てを返します（ゼロに向かって丸める）。$n > 0$であり、$n$が偶数の場合は$x \geq 0$である必要があります。

# 例

```jldoctest
julia> iroot(ZZ(13), 3)
2
```
